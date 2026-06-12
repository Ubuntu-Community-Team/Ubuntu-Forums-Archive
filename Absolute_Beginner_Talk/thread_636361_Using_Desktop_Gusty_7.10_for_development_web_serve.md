---
title: "Using Desktop Gusty 7.10 for development web server"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by desk2web on 2007-12-09
I am trying to work my way around Ubuntu, and so far am really happy - the learning curve is steep but managable.

Now, my latest "problem" is using 7.10 desktop as a development webserver for testing out my web sites before uploading to my live server.

I have installed:

apache2
apache2.2-common
curl
php5
php5-common
php5-curl
php5-mysql
php5-odbc
mysql-admin
mysql-admin-common
mysql-client
mysql-client-5.0
mysql-common
mysql-doc-5.0
mysql-server
mysql-server-5.0
phpmyadmin

I am able to see the default "it works" page via [http://192.168.0.3/apache2-default/](http://192.168.0.3/apache2-default/) 

However, I am not able to save any file into the apache2-default folder (var/www/apache2-default), nor can I create a new folder in /var/www to be able to work on.

Have I installed the best component parts?  
How can I configure apache to allow for additonal hosts (vhosts I guess they are).
How can I write to these locked folders?

Thanks for taking the time to read this post, and thanks in advance for any advice you are able to pass on to me.

Allan

---

### Post by winkman on 2007-12-09
Congratulations! You've done really well! 
I've just followed the same process, trying to get a decent LAMP system up and running (whilst also running a home computer!)...

The problem you have is with file permissions...
You don't have (user) access to the /var/www/ folder, so you must change the file permissions for this.
The easiest way i can think to do this is:
(sorry if this is a little off... i'm working on a Micro$oft computer a.t.m)
Open a terminal.
type:
gksu nautilus
(enter your password)
in Nautilus, navigate to /var/
Right click on the www folder, and click Properties
Navigate to the Permissions tab, and and change the owner user to yourself (ie. NOT root)
Click the button (sorry, i can't remember the exact wording) that says something about applying this to below file permissions.
Click Apply, and then OK.
You may need to repeat this on other subfolders.
Close the root nautilus window, and reopen nautilus in your user account. (not root)
You should be able to access the folder, with read/write/execute access... :)
Hope this all works out, 
It took me a while to figure it out, and even longer to fiddle with the settings, but it now works.

If it doesn't, perhaps you can find a tutorial about file permissions?
Alternatively, you could use the server tutorials under the Community Documentation to create a webspace under your home directory. 

Hope this works!
Mitch

---

