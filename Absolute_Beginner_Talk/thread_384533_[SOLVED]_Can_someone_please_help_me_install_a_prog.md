---
title: "[SOLVED] Can someone please help me install a program?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-03-14
Hi All,

Im still having all sorts of problems installing software from tar.gz files.  Ive been trying to install Joomla and have gone through some of the walkthroughs provided online and even a walkthrough for installing this package but im getting no-where!  Please Help!

Ive downloaded the file Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz which is sitting nicely on my desktop.  Ive been into terminal and updated my build essential packages and ive even un-packed this file to a file called Joomla which is sitting in /home/bespin/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz_FILES just in case I need them.  I have however gone through a walkthough which suggested using the file on my desktop and running the following (obscure-1.0.tar.gz being an example file to be replaced with my file name):  

tar -xvzf obscure-1.0.tar.gz
cd obscure-1.0
./configure
make
sudo make install

Unfortunaely, when I tried that, this is what I got.....

bespin@mike-desktop:~$ tar -xvzf Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz
tar: Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
bespin@mike-desktop:~$

Does anyone know how to do this?  Id really like to get to the bottom of this and install a file from tar.gz - this would be my first one, all the rest have failed miserably and I know it must be so easy once you have got used to it!!!  

Pleas help!

---

### Post by Strider on 2007-03-14
From the console, do you see the file there when you do an "ls -al"?  Maybe there's a typo with the filename.  Make sure the file exist in current directory you're running "tar" from.

-Mike

---

### Post by MikeSz on 2007-03-14
Hi Strider - this is what I get...

bespin@mike-desktop:~$ ls -al
total 148
drwxr-xr-x 23 bespin bespin 4096 2007-03-14 19:42 .
drwxr-xr-x  4 root   root   4096 2007-03-14 18:06 ..
-rw-------  1 bespin bespin  373 2007-03-14 19:41 .bash_history
-rw-r--r--  1 bespin bespin  220 2007-03-14 18:06 .bash_logout
-rw-r--r--  1 bespin bespin  414 2007-03-14 18:06 .bash_profile
-rw-r--r--  1 bespin bespin 2227 2007-03-14 18:06 .bashrc
drwxr-xr-x  4 bespin bespin 4096 2007-03-14 19:21 Bespin
drwxr-xr-x  3 bespin bespin 4096 2007-03-14 18:12 .config
-rw-r--r--  1 bespin bespin   59 2007-03-14 19:42 .DCOPserver_mike-desktop__0
lrwxrwxrwx  1 bespin bespin   40 2007-03-14 19:42 .DCOPserver_mike-desktop_:0 ->
 /home/bespin/.DCOPserver_mike-desktop__0
drwxr-xr-x  2 bespin bespin 4096 2007-03-14 19:41 Desktop
-rw-------  1 bespin bespin   24 2007-03-14 18:07 .dmrc
-rw-------  1 bespin bespin   16 2007-03-14 18:07 .esd_auth
lrwxrwxrwx  1 bespin bespin   26 2007-03-14 18:06 Examples -> /usr/share/example
-content
drwx------  3 bespin bespin 4096 2007-03-14 19:11 .gaim
drwx------  4 bespin bespin 4096 2007-03-14 19:21 .gconf
drwx------  2 bespin bespin 4096 2007-03-14 19:50 .gconfd
-rw-r-----  1 bespin bespin    0 2007-03-14 19:34 .gksu.lock
drwx------  8 bespin bespin 4096 2007-03-14 19:29 .gnome2
drwx------  2 bespin bespin 4096 2007-03-14 18:07 .gnome2_private
drwxr-xr-x  2 bespin bespin 4096 2007-03-14 18:07 .gstreamer-0.10
-rw-r--r--  1 bespin bespin   88 2007-03-14 18:07 .gtkrc-1.2-gnome2
-rw-------  1 bespin bespin  543 2007-03-14 19:42 .ICEauthority
drwxr-xr-x  3 bespin bespin 4096 2007-03-14 18:40 .icons
drwx------  3 bespin bespin 4096 2007-03-14 19:22 .kde
drwx------  3 bespin bespin 4096 2007-03-14 18:22 .macromedia
drwxr-xr-x  3 bespin bespin 4096 2007-03-14 19:30 .mcop
-rw-------  1 bespin bespin   31 2007-03-14 19:30 .mcoprc
drwx------  3 bespin bespin 4096 2007-03-14 18:07 .metacity
drwx------  4 bespin bespin 4096 2007-03-14 18:22 .mozilla
drwxr-xr-x  3 bespin bespin 4096 2007-03-14 18:07 .nautilus
drwxr-xr-x  2 bespin bespin 4096 2007-03-14 19:22 .qt
-rw-------  1 bespin bespin  531 2007-03-14 19:29 .recently-used
-rw-r--r--  1 bespin bespin    0 2007-03-14 18:18 .sudo_as_admin_successful
drwxr-xr-x  4 bespin bespin 4096 2007-03-14 18:40 .themes
drwx------  3 bespin bespin 4096 2007-03-14 18:11 .thumbnails
drwx------  2 bespin bespin 4096 2007-03-14 18:07 .Trash
drwx------  2 bespin bespin 4096 2007-03-14 18:17 .update-notifier
-rw-------  1 bespin bespin  167 2007-03-14 19:20 .Xauthority
-rw-------  1 bespin bespin 5299 2007-03-14 19:48 .xsession-errors
bespin@mike-desktop:~$

So I guess it isnt there?  And yet I know it is because im staring at it on my desktop :confused:

---

### Post by aysiu on 2007-03-14
This is what the INSTALL.php file says: ```
<?php
/**
* @version $Id: INSTALL.php 5973 2006-12-11 01:26:33Z robs $
* @package Joomla
* @copyright Copyright (C) 2005 Open Source Matters. All rights reserved.
* @license http://www.gnu.org/copyleft/gpl.html GNU/GPL, see LICENSE.php
* Joomla! is free software. This version may have been modified pursuant
* to the GNU General Public License, and as distributed it includes or
* is derivative of works licensed under the GNU General Public License or
* other free or open source software licenses.
* See COPYRIGHT.php for copyright notices and details.
*/

// no direct access
defined( '_VALID_MOS' ) or die( 'Restricted access' );
?>

REQUIREMENTS
------------

First you must have the base environment for Joomla!.
We have thoroughly tested Joomla! on: Linux, Free BSD, Mac OS X and Windows NT/2000.
Linux or one of the BSD's are recommended, but anything else that can run the
3 pieces of software listed below should do it.

Apache	-> http://www.apache.org
MySQL	-> http://www.mysql.com
PHP	-> http://www.php.net


SERVER CONFIGURATION
--------------------

You MUST ensure that PHP has been compiled with support for MySQL and Zlib
in order to successfully run Joomla!.

While we have reports that Joomla! works on IIS server we recommend Apache
for running Joomla! on Windows.


OPTIONAL COMPONENTS
-------------------

If you want support for SEF (Search Engine Friendly) URLs, you'll need mod_rewrite and the ability to
use local .htaccess files.


INSTALLATION
------------

1. DOWNLOAD Joomla!

	You can obtain the latest Joomla! release from:
		http://www.joomla.org

	Copy the tar.gz file into a working directory e.g.

	$ cp JoomlaVx.x.x-Stable.tar.gz /tmp/Joomla

	Change to the working directory e.g.

	$ cd /tmp/Joomla

	Extract the files e.g.

	$ tar -zxvf JoomlaVx.x.x-Stable.tar.gz

	This will extract all Joomla! files and directories.  Move the contents
	of that directory into a directory within your web server's document
	root or your public HTML directory e.g.

	$ mv /tmp/Joomla/* /var/www/html

	Alternatively if you downloaded the file to your computer and unpacked
	it locally use a FTP program to upload all files to your server.
	Make sure all PHP, HTML, CSS and JS files are sent in ASCII mode and
	image files (GIF, JPG, PNG) in BINARY mode.


2. CREATE THE Joomla! DATABASE

	Joomla! will currently only work with MySQL.  In the following examples,
	"db_user" is an example MySQL user which has the CREATE and GRANT
	privileges.  You will need to use the appropriate user name for your
	system.

	First, you must create a new database for your Joomla! site e.g.

	$ mysqladmin -u db_user -p create Joomla

	MySQL will prompt for the 'db_user' database password and then create
	the initial database files.  Next you must login and set the access
	database rights e.g.

	$ mysql -u db_user -p

	Again, you will be asked for the 'db_user' database password.  At the
	MySQL prompt, enter following command:

	GRANT ALL PRIVILEGES ON Joomla.*
		TO nobody@localhost IDENTIFIED BY 'password';

	where:

	'Joomla' is the name of your database
	'nobody@localhost' is the userid of your webserver MySQL account
	'password' is the password required to log in as the MySQL user

	If successful, MySQL will reply with

	Query OK, 0 rows affected

	to activate the new permissions you must enter the command

	flush privileges;

	and then enter '\q' to exit MySQL.

	Alternatively you can use your web control panel or phpMyAdmin to
	create a database for Joomla!.


3. WEB INSTALLER

Finally point your web browser to http://www.mysite.com where the Joomla! web
based installer will guide you through the rest of the installation.


4. CONFIGURE Joomla!

You can now launch your browser and point it to your Joomla! site e.g.

	http://www.mysite.com -> Main Site
	http://www.mysite.com/administrator -> Admin

You can log into Admin using the username 'admin' along with the
password that was generated or you chose during the web based install.


Joomla! ADMINISTRATION
----------------------

Upon a new installation, your Joomla! website defaults to a very basic
configuration with only a few active components, modules and templates
(CMTs).

Use Admin to install and configure additional CMTs, add users, select
default language and much more.

Note that additional community-contributed CMTs and languages are
available via http://www.joomla.org

```

---

### Post by MikeSz on 2007-03-14
ok - my fault - did a location search from file manager and had got the wrong desktop folder.  However, the problem is now slightly different.  this is what I got from the tar command (it was a huge stream of files and things so had to cut them...)

bespin@mike-desktop:~/Desktop$ tar -xvzf Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz
administrator/
...........
templates/css/offline.css
bespin@mike-desktop:~/Desktop$ cd Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz
bash: cd: Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz: Not a directory
bespin@mike-desktop:~/Desktop$

The next thing it said to run was cd obscure-1.0, obsucre being the dummy file.  So I changed it (as you can see) and im stuck again!!  What do I do now?  I also have a mass of files and folders on my desktop!

---

### Post by MikeSz on 2007-03-14
aysiu - is this what you mean?

<?php
/**
* @version $Id: INSTALL.php 5973 2006-12-11 01:26:33Z robs $
* @package Joomla
* @copyright Copyright (C) 2005 Open Source Matters. All rights reserved.
* @license [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) GNU/GPL, see LICENSE.php
* Joomla! is free software. This version may have been modified pursuant
* to the GNU General Public License, and as distributed it includes or
* is derivative of works licensed under the GNU General Public License or
* other free or open source software licenses.
* See COPYRIGHT.php for copyright notices and details.
*/

// no direct access
defined( '_VALID_MOS' ) or die( 'Restricted access' );
?>

REQUIREMENTS
------------

First you must have the base environment for Joomla!.
We have thoroughly tested Joomla! on: Linux, Free BSD, Mac OS X and Windows NT/2000.
Linux or one of the BSD's are recommended, but anything else that can run the
3 pieces of software listed below should do it.

Apache	-> [http://www.apache.org](http://www.apache.org)
MySQL	-> [http://www.mysql.com](http://www.mysql.com)
PHP	-> [http://www.php.net](http://www.php.net)


SERVER CONFIGURATION
--------------------

You MUST ensure that PHP has been compiled with support for MySQL and Zlib
in order to successfully run Joomla!.

While we have reports that Joomla! works on IIS server we recommend Apache
for running Joomla! on Windows.


OPTIONAL COMPONENTS
-------------------

If you want support for SEF (Search Engine Friendly) URLs, you'll need mod_rewrite and the ability to
use local .htaccess files.


INSTALLATION
------------

1. DOWNLOAD Joomla!

	You can obtain the latest Joomla! release from:
		[http://www.joomla.org](http://www.joomla.org)

	Copy the tar.gz file into a working directory e.g.

	$ cp JoomlaVx.x.x-Stable.tar.gz /tmp/Joomla

	Change to the working directory e.g.

	$ cd /tmp/Joomla

	Extract the files e.g.

	$ tar -zxvf JoomlaVx.x.x-Stable.tar.gz

	This will extract all Joomla! files and directories.  Move the contents
	of that directory into a directory within your web server's document
	root or your public HTML directory e.g.

	$ mv /tmp/Joomla/* /var/www/html

	Alternatively if you downloaded the file to your computer and unpacked
	it locally use a FTP program to upload all files to your server.
	Make sure all PHP, HTML, CSS and JS files are sent in ASCII mode and
	image files (GIF, JPG, PNG) in BINARY mode.


2. CREATE THE Joomla! DATABASE

	Joomla! will currently only work with MySQL.  In the following examples,
	"db_user" is an example MySQL user which has the CREATE and GRANT
	privileges.  You will need to use the appropriate user name for your
	system.

	First, you must create a new database for your Joomla! site e.g.

	$ mysqladmin -u db_user -p create Joomla

	MySQL will prompt for the 'db_user' database password and then create
	the initial database files.  Next you must login and set the access
	database rights e.g.

	$ mysql -u db_user -p

	Again, you will be asked for the 'db_user' database password.  At the
	MySQL prompt, enter following command:

---

### Post by MikeSz on 2007-03-14
Ok, the tar thingy simply unpacked all the components of the tar.gz file to my desktop didnt it?  I seem to already have done that by right clicking on the tar.gz file and extracting it to my chosen directory.  So I have a directory - /home/bespin/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz_FILES which has all the directories and files.  Ive tried navigating to the directory and running ./configure - no joy.  Ive copied the results below...Can anyone please help with this, I seem to be getting no-where!

bespin@mike-desktop:~/Desktop$ cd Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz
bash: cd: Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz: Not a directory
bespin@mike-desktop:~/Desktop$ cd /home/bespin/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz_FILES
[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$ ./configure
bash: ./configure: No such file or directory
[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$ make
make: *** No targets specified and no makefile found. Stop.
[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$ cd /home/bespin/Bespin/apps
bespin@mike-desktop:~/Bespin/apps$ ./configure
bash: ./configure: No such file or directory
bespin@mike-desktop:~/Bespin/apps$

---

### Post by MikeSz on 2007-03-14
Please can someone tell me what I should be doing next to install this thing?  Im determined not to give up so any help would be really appreciated!

---

### Post by MikeSz on 2007-03-15
Can anyone help with this - please, please please ????

Im at my wits end with these tar.gz files...

---

### Post by eljalill on 2007-03-15
can you go to that directory again, do a
ls
and tell us what the output is?

---

### Post by MikeSz on 2007-03-15
Hi There eljalill, which directory do you want the content of, my desktop with the tar.gz file on it or the Joomla directory that I created and extracted all the files into?

---

### Post by eljalill on 2007-03-15
The Joomla directory you created, when you extracted the files from the tar.gz file, please .

---

### Post by MikeSz on 2007-03-15
No problems - I have to go out for a little while unfortunately so i will post it as soon as I get back - thanks for the help though and hopefully with a little luck later on it can be sorted out...

---

### Post by eljalill on 2007-03-15
Since I also have to leave in the near future, here is what you should do:
Look at the ls output from above (or better: also post it)

Is there a executable "configure" file?
If yes, do the same again (./configure).

If not, what is, what your error message suggests,
post the output, and wait for help, or try to execute anything that looks like a setup file. (setup.ini or so...)

---

### Post by MikeSz on 2007-03-15
Hi there, sorry for the delay, been a bit of a mad day.  Anyway, Ive navigated to the directory that I unpacked the original tar.gz into and tried ./configure.  This is what I got...

bespin@mike-desktop:~$ cd /home/bespin/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz_FILES
[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$ ./configure
bash: ./configure: No such file or directory
[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$

I also tried the command you suggested and this is the output...

[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$ ls -as
total 224
  4 .                         4 globals.php     4 language
  4 ..                        8 help            4 mambots
  4 administrator             8 htaccess.txt    4 modules
104 CHANGELOG.php             4 images          4 offlinebar.php
  4 components                4 includes        8 offline.php
  8 configuration.php-dist    8 index2.php      4 pathway.php
  4 COPYRIGHT.php            12 index.php       4 templates
  4 editor                    8 INSTALL.php
[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$

Any suggestions as to what I should do next would be, by me, greatly appreciated!!!

---

### Post by jhenager on 2007-03-15
When you get to this directory:
[email]bespin@mike-desktop:~/Bespin/apps/Jo...Package.tar.gz[/email]_FILES$
instead of trying ./configure, do a ls to see if configure is there.

I have always tried something like Synaptic or Add/Remove first when installing programs. Sure, it isn't as cool and geeky, but it might save you some aggravation.

---

### Post by MikeSz on 2007-03-15
The output of an "ls" command is as follows....

[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$ ls
administrator           editor        includes     mambots         templates
CHANGELOG.php           globals.php   index2.php   modules
components              help          index.php    offlinebar.php
configuration.php-dist  htaccess.txt  INSTALL.php  offline.php
COPYRIGHT.php           images        language     pathway.php
[email]bespin@mike-desktop:~/Bespin/apps/Joomla_1.0.0_to_1.0.12-Stable-Patch_Package.tar.gz[/email]_FILES$

Id love to try synaptic - in fact ive looked for Joomla on there but its nowhere to be found :confused:   So as it seemed like the only way of getting Joomla to run, im trying to compile it.  If anyone out there has a .deb file or something that I can use then that would obviously be greatly appreciated!!!

---

### Post by jhenager on 2007-03-15
If "ls configure" says No such file or folder, then something else needs to happen before you will be able to run ./configure.

---

### Post by jhenager on 2007-03-15
See post below. This program isn't like a standalone program. It needs Apache and PhP.

---

### Post by jhenager on 2007-03-15
[http://help.joomla.org/content/view/39/132/](http://help.joomla.org/content/view/39/132/)
^the easy way
[http://help.joomla.org/content/view/40/132/](http://help.joomla.org/content/view/40/132/)
^the less easy way

---

