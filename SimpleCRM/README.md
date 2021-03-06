Title: SimpleCRM

Author: Grant James Kimball

Author URI: http://yourlocalwebmaster.com

Description: SimpleCRM is just as the title implies, a simple client relations managament system.

-SUMMARY-

	There are two (2) user levels:  ADMIN & USER

	1. An admin can CRUD USERS, edit DEFAULT LIST VALUES and import USERS.
	2. A User can CRUD new contacts AND their own unique DEFAULT LIST VALUES and export to CSV


	DEFAULT LIST VALUES are custom drop down / field options that a user can assign to a "CONTACT". 
	i.e. (Type of Customer, Sales Stage, Group, etc...) 

-INSTALLATON-

	1. Create a Database on your server and edit the config file located at /php/class/db.php (see below)
	
		private $hostname_logon_live = 'database_host'; 
		private $database_logon_live = 'database_name'; 
		private $username_logon_live = 'database_username'; 
		private $password_logon_live = 'database_password';

	2. Standard Configuration. Open php/class/general.php and configure the following lines:

			$this->site_title = "My SITE";		
			$this->siteurl = "http://mysite.biz/";
			$this->server_email = "email@mysite.biz";
			
			// Recommended size: 187x21
			$this->logo_nav_html = '<img src="images/mylogo.png" alt="My Logo" />';

			$this->welcome_logo_html = '<img src="images/mylogo.png" alt="My Welcome Logo" />';
				

	3. SimpleCRM has FTP upload and transfer capabilities. This is DISABLED by default and requires access to your server. 
	   To configure FTP please see below (CONFIGURING FTP EXPORT). 

	4. Upload the files to your server.		
          
-INITIAL LOGIN-

	Admin Level User
		u: admin@mysite.biz 
		p: simpleCRM123

	User Level User
		u: user@mysite.biz
		p: simpleCRM123

-IMPORT USERS-

	To upload bulk users, you will need a Comma Delimitted CSV template with the following headers:  "email, password, level, active"
	ex: (import_users.csv)

	---------------- import_users.csv ------------
	email,password,level,active
	admin@domain.com,mypassword,2,1
	user@domain.com,mypassword,1,1
	-----------------------------------------------
	-Description of fields-
		Email is the user email
		Password is the unencrypted user password
		Level is 1 or 2, 1 being USER, and 2 being ADMIN
		Active is a bool value, 1 or 0, respectfully.

-CONFIGURING FTP EXPORT-

	1. Open "/php/class/general.php"
		CHANGE:	$this->ftp = false;
		TO: $this->ftp = true;

	2. Open the files "export_contact.php" AND "php/local_api/export_contact.php"
	3. Edit the following lines to your server information:

		$ftp_host = "123.456.789.0";		
		$ftp_user = "ftp_user_name";
		$ftp_pass = "ftp_user_pass";
		$ftp_folder = "my_exports_folder";

