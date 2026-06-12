---
title: "Help me fix VHCS control panel please..."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by latheesan on 2007-12-15
I recently bought a dedicated server and decided to pay my host 40 euro to install VHCS control panel.

At first, everything worked, just like that. 2 days ago, when i logged in as admin and i clicked the  menu button "Manage Users", the internet explorer said:

> Internet Explorer cannot display the webpage 
   
   Most likely causes:
You are not connected to the Internet. 
The website is encountering problems. 
There might be a typing error in the address.

I thought it was my computer or IE itself, so i tried doing this in firefox and as soon as i clicked "Manage Users" button, the page became blank. I tried to view the source, even the page source was blank.

I thought maybe it was something wrong with my admin account, i had to urgently make a ftp account on a domain i added, so i logged with my domain.com and my pass and SAME error. 

What i did notice was this error was caused at this url :

http://<server ip>/vhcs2/chk_login.php

So i got on SFTP and logged in as root and went to the dir /var/www/vhcs2/gui/ and opened the chk_loging.php and wanted to see why it is erroring there, this is what i found:

[PHP]include 'include/vhcs-lib.php';
if (isset($_POST['uname']) && isset($_POST['upass'])) {
	$uname = get_punny($_POST['uname']);
	if (register_user($uname, $_POST['upass'])) {
	if ($_SESSION['user_type'] == 'admin') {
            header("Location: admin/index.php");
        } else if ($_SESSION['user_type'] == 'reseller') {
            header("Location: reseller/index.php");
        } else if ($_SESSION['user_type'] == 'user') {
            header("Location: client/index.php");
        }
   } else {
		header('Location: index.php');
   }
} else {
      header('Location: index.php');
}
exit(0);[/PHP]

As you can see, there is nothing out of the ordinary here, so i didn't know why it was erroring. As a last attempt to fix this, i went to /var/www/vhcs2/gui/includes/ and opened vhcs-lib.php file and turned on error reporting with error_reporting(E_ALL);

I tried to login and again, same thing, no error message, IE says page cannot be displayed, and firefox gives me a blank page. 

Can someone please help? Im out of options...

---

