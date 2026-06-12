---
title: "sigh... php issues"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by 1oki on 2007-09-05
ok, I am following this guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server)
I get to the point where I have to enable php, a2enmod php5, and I get a "Module does not exist!".

Any ideas?

---

### Post by KCPokes on 2007-09-05
I assume you followed the first steps?

```

sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```

The step you are throwing errors on is only if your server will still not load PHP pages:

```

    * To test if php5 installed correctly 

gksudo gedit /var/www/testphp.php

    * (Optional) Insert the following line into the new file 

<?php phpinfo(); ?>

```

The first three steps should take care of your needs.  Create your php file and verify the results by placing the file in your docroot (/var/www).

---

### Post by 1oki on 2007-09-05
yeah I have done all that... I go to open the test php page, and it prompts me to open it with another program or to save it... So I followed the next step in the tutorial... a2enmod php5 and I get the "module does not exist!". 


lol get me?

---

### Post by annda on 2007-09-05
do you have php in your /etc/apache2/mods-enabled/ ?

---

### Post by 1oki on 2007-09-05
nope... thats what I am trying to do... :) heh

I also do not have it in my /etc/apache2/mods-available/    if that means anything...  dunno why its not putting it in those locations. reinstalling doesn't help either.

---

### Post by KCPokes on 2007-09-05
> **1oki said:**
> nope... thats what I am trying to do... :) heh

I also do not have it in my /etc/apache2/mods-available/    if that means anything...  dunno why its not putting it in those locations. reinstalling doesn't help either.

Seems to me that your Apache isn't installed correctly.  Can you serve up ANY html pages, aside from PHP?

---

### Post by annda on 2007-09-05
you mean reinstalling php5 or apache2?

in that case, i would sugest uninstalling+purging configs for both (and any older versions you might have) and installing again.

anyway, it is pretty uncommon unless you have older versions - apache and/or php...

---

### Post by 1oki on 2007-09-05
> **KCPokes said:**
> Seems to me that your Apache isn't installed correctly.  Can you serve up ANY html pages, aside from PHP?

yeah Apache2 is working fine...  I have already uninstalled + purged apache2 config file, and reinstall. I did this prior... I am about to give up. The SQL gods do not want me learning php to use with SQL (my ultimate goal). I will try to remove all apache files, and php files and try again...

---

### Post by KCPokes on 2007-09-05
I'd recommend cleaning up what you've done this far and try to run:
```

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

```

That is your typical LAMP set up there.  In fact, if you are running Feisty, they even have this option:
```

sudo tasksel install lamp-server

```

---

### Post by 1oki on 2007-09-05
I will give that a try!

---

### Post by 1oki on 2007-09-05
well now  it doesn't prompt me to open or save... just gives me a 500 internal server error when i try to open a php file.... also, it says apache2 is installed, but I don't see any evidence of it. But, it is... because i can browse it from firefox... basically, I cant find the config files! I am getting a headache...

---

### Post by KCPokes on 2007-09-05
Check the apache logs.  Should tell you what the 500 error is in reference to.  It could be a simple as a typo error at this point.

---

### Post by 1oki on 2007-09-05
yeah I think i botched up the Apache2 install........... its saying it can't locate /usr/share/apache2

I guess I will quite for tonight and work on it tomorrow... Oh, it also said premature eof on the test php file... I should figure it out. My brain just hurts atm. Thanks for now! If i cant figure it out from here I will post another one up! :)

---

### Post by 1oki on 2007-09-06
> **KCPokes said:**
> I'd recommend cleaning up what you've done this far and try to run:
```

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

```

That is your typical LAMP set up there.  In fact, if you are running Feisty, they even have this option:
```

sudo tasksel install lamp-server

```

so i retried the first suggestion and here is my output...

```
root@skynet:/var/www# apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-common mysql-client-5.0
  mysql-server-5.0
Suggested packages:
  tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common
  libapache2-mod-php5 mysql-client-5.0 mysql-server mysql-server-5.0
  php5-mysql
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/37.5MB of archives.
After unpacking 97.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-client-5.0.
(Reading database ... 129813 files and directories currently installed.)
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.3-3.2ubuntu0.1_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.3-3.2ubuntu0.1_i386.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.3-3.2ubuntu0.1_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.2.3-3.2ubuntu0.1_all.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.1-0ubuntu1.4_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1_all.deb) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.2.1-0ubuntu1.4_i386.deb) ...
Setting up mysql-client-5.0 (5.0.38-0ubuntu1) ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up apache2-utils (2.2.3-3.2ubuntu0.1) ...
Setting up apache2.2-common (2.2.3-3.2ubuntu0.1) ...
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!
This module is already enabled!

Setting up apache2-mpm-prefork (2.2.3-3.2ubuntu0.1) ...

Setting up apache2 (2.2.3-3.2ubuntu0.1) ...
Setting up libapache2-mod-php5 (5.2.1-0ubuntu1.4) ...
Error: The new file /usr/share/php5/php.ini-dist does not exist!
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mysql-server (5.0.38-0ubuntu1) ...
Setting up php5-mysql (5.2.1-0ubuntu1.4) ...

Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

just some info for all you trying to help me :) I know this should be an easy task, but nothing is ever easy for me! thanks a bunch!

---

### Post by 1oki on 2007-09-06
hehe, figured out why apache wouldnt work... no httpd.conf file in /etc/apache2/... made a blank httpd.conf file and that fixed it. but now I am stuck with the php issue... so now I can continue with my venture.

---

### Post by 1oki on 2007-09-06
ok... got it working... kinda... now it will work if i go to [http://127.0.0.1/](http://127.0.0.1/) but not if i go to [http://localhost/](http://localhost/)

---

### Post by 1oki on 2007-09-06
OK! never mind... just a quick clear of the cache and it was all good! Done and done! thanks all

---

### Post by dennis_matutina on 2007-09-07
Hi!

I've been following this thread and my only problem was apache2 could not parse php files.

I can open html files with no problem.

I did an install, reinstall, tasksel, etc... to no avail. PHP files are being downloaded, or the browser prompts for an application to open it :(

Any other ideas, please? 

Thanks in advance :)

---

### Post by dennis_matutina on 2007-09-07
and yes, I do clear the cache of my browser...

---

### Post by 1oki on 2007-09-07
did you enable the php module, a2enmod php5 ? If so what is the output... after uninstalling and reinstalling I like to run apt-get remove, and apt-get autoclean ... out puts of when you install apache2 and all other packages for this case would be great as well :)

---

### Post by Dr Small on 2007-09-07
> **1oki said:**
> ok, I am following this guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server)
I get to the point where I have to enable php, a2enmod php5, and I get a "Module does not exist!".

Any ideas?
The easiest way to install Apache, Php, MySQL, PhpMyAdmin and such, is to follow my tutorial that I wrote and posted on my blog:

[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

Dr Small

---

### Post by 1oki on 2007-09-07
I already figured out my issues and got it working, thanks though! I am trying to help dennis now :)

---

### Post by dennis_matutina on 2007-09-13
gee thanks! ;-)

As I said, I've been following this thread. I guess the fact that I've been using RH/Fedora distros until now which made the Feisty install of apache2 and php5 seem complicated.

It took at least a week of install/re-install/purge to no avail...

And the solutions posted by all of you really helped me track down the problem.

It all boils down to finding and uncommenting or typing this to apache2.conf (yes, someone already posted this solution but I was blind :( ):

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

Prior to that, the files from /etc/apache2/mods-available must be symlinked into that directory as posted by the others in this thread.

I made the mistake of assuming that apt-get install/remove will make the problem go away. I also had trouble initially running apache2 without apache. Tinkering with apache2.conf solved both of these issues for me.

Finally, this is the compact answer: [https://answers.launchpad.net/ubuntu/+question/11875](https://answers.launchpad.net/ubuntu/+question/11875) .Many people have been assisting Ubuntu newbies like me, but sometimes, it takes time for their advice to settle down through our thick skulls :)

Thank you everyone! :popcorn:

---

