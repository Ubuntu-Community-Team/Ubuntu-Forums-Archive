---
title: "PHP4 with Apache"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-12-17
I have installed Apache and it works fine.  However, whenever I try to open a .php file from my browser (a file that is on my server) it asks where I want to save the file to, rather than just displaying it in the browser.  I have followed the instructions on the ubuntu beginners guide, but my php still isn't working.  Does anyone know a good site that has a tutorial on how to configure php4 with apache in ubuntu linux?

Thank you.

---

### Post by NotJustANewbie on 2005-12-17
[http://www.hostlibrary.com/installing_apache_mysql_php_on_linux](http://www.hostlibrary.com/installing_apache_mysql_php_on_linux)

Does no-one use Google any more?!?

---

### Post by Swab on 2005-12-17
This might be more appropriate [www.ubuntuguide.org]("http://www.ubuntuguide.org")

---

### Post by amcavoy on 2005-12-18
Yes, I have already followed the steps in [http://www.ubuntuguide.org/#installapachehttpserver](http://www.ubuntuguide.org/#installapachehttpserver) but it still isn't working.  Also, I tried the other site suggested, and most of that is for older versions and the commands wouldn't work in my terminal (it didn't recognize --prefix).

---

### Post by Enter on 2005-12-18
[QUOTE=NotJustANewbie][http://www.hostlibrary.com/installing_apache_mysql_php_on_linux](http://www.hostlibrary.com/installing_apache_mysql_php_on_linux)

Does no-one use Google any more?!?[/QUOTE]
saying google it is against rules here :P :lol:
[http://www.ubuntuforums.org/showthread.php?t=65842](http://www.ubuntuforums.org/showthread.php?t=65842)

---

### Post by amcavoy on 2005-12-18
It's a good point though.  However, I have tried Google and came up with the Ubuntu Beginner's Guide (ubuntuguide.org), which did not help to fix the problem, and also a mess of other sites that explained installation for different versions / different flavors of Linux.

I have done the following:
```
sudo apt-get install apache
```
```
sudo apt-get install apache2
```
```
sudo apt-get install php4
```
My Apache server works great, in that it allows me to access my website and files from a browser.  The problem is that it only displays .html files, and won't handle .php files, although I have installed PHP4.  I am running Breezy and have followed the instructions **exactly** as they are in the Ubuntu Beginner's Guide.

I would appreciate any ideas / suggestions about this if possible.  Also, for those who have installed an Apache server and PHP4 on Breezy, could you show me where you went to find instructions (if you aren't a Linux guru) and / or your steps?

Thank you very much, and any help is greatly appreciated :smile:.

Alex

---

### Post by Swab on 2005-12-20
[QUOTE=amcavoy]It's a good point though.  However, I have tried Google and came up with the Ubuntu Beginner's Guide (ubuntuguide.org), which did not help to fix the problem, and also a mess of other sites that explained installation for different versions / different flavors of Linux.

I have done the following:
```
sudo apt-get install apache
```
```
sudo apt-get install apache2
```
```
sudo apt-get install php4
```
My Apache server works great, in that it allows me to access my website and files from a browser.  The problem is that it only displays .html files, and won't handle .php files, although I have installed PHP4.  I am running Breezy and have followed the instructions **exactly** as they are in the Ubuntu Beginner's Guide.

I would appreciate any ideas / suggestions about this if possible.  Also, for those who have installed an Apache server and PHP4 on Breezy, could you show me where you went to find instructions (if you aren't a Linux guru) and / or your steps?

Thank you very much, and any help is greatly appreciated :smile:.

Alex[/QUOTE]

I don't know if you got this sorted... but you have installed 2 different versions of apache...

---

### Post by philwozza on 2005-12-20
Do you still need some assistance?

It seams you have installed two versions of apache. I would recommend that you remove the older of the two versions by typing ( into a terminal window )

sudo apt-get remove apache

then to enable PHP4 support in apache2 enter the command ( into a terminal window )

sudo apt-get install libapache2-mod-php4

Then restart Apache2 using the command

sudo /etc/init.d/apache2 restart

You should find that the php pages on your website work now.
Please let us know if this works for you.

---

### Post by Gandalf on 2005-12-20
what philwozza suggested is what you have to do actually, apache cannot run php files without having libapache2-mod-php4, so be sure to:
sudo apt-get install apache2 php4 libaapache2-mod-php4

if you need mysql then 
sudo apt-get instamm php4-mysql

TIP:
type apt-cache search php4

to get a list of all php4 modules that can be installed

good luck

---

### Post by amcavoy on 2005-12-21
I hope I'm just making a simple mistake here, because I absolutely cannot get this to work.  I have attached screenshots of both my terminal and the browser when I try to open a .php file on my server.  I'd really appreciate it if someone could take a look at those:

**Terminal**

[http://server5.theimagehosting.com/image.php?img=terminal.png](http://server5.theimagehosting.com/image.php?img=terminal.png)

**Browser**

[http://server5.theimagehosting.com/image.php?img=browser.1.png](http://server5.theimagehosting.com/image.php?img=browser.1.png)

Thank you very much for the assistance :smile:.

---

### Post by harisund on 2005-12-21
Look, start afresh, that is what I always do: 

apt-get --purge remove apache apache2 apache2-common php4
apt-get install apache2 php4

That sort of works for me. 

Could you tell if it works for you too? (With the universe repositaries on Breezy.)

---

### Post by amcavoy on 2005-12-21
It looks like it worked!  Here is the link to my testphp document, which seems to be loading fine:

[http://apm.homedns.org/testphp.php](http://apm.homedns.org/testphp.php)

Thank you very much!!

---

### Post by harisund on 2005-12-21
Yes. Apparently there were some configuration problems, with installing 2 versions of apache and all that. 

Also, I learnt, in another post through Ubuntuforums of course, that the /etc/apache2 directory, which holds all your configuration files, will not get removed with apt-get --purge remove apache2

The reason for that is this 
dpkg -S /etc/apache2

This outputs the name of the package which created /etc/apache2, and that happens to be apache2-common. Hence when you purged that, you pretty much wiped apache2 of your disk and reinstalled it. apt-get installs apache2-common when you ask it to install apache2,but doesn't do the same when you ask it to uninstall !!

---

### Post by hbush on 2006-01-12
[QUOTE=NotJustANewbie][http://www.hostlibrary.com/installing_apache_mysql_php_on_linux](http://www.hostlibrary.com/installing_apache_mysql_php_on_linux)

Does no-one use Google any more?!?[/QUOTE]

this is not an answer by the way..... every one here knows google. 

ppl we are here to share our knowledge, if yo found an answer on google post the link, I know that you are smarter than all of us newbees here because you started using linux earlier than we did but thats not a reason to post such an answer, we are seeking knowledge and keep in mind that there are ppls like me that prefere to find it in ubuntu rather than in google. So if you have an experience and you are here to share it ... I and most of us newbees will apreciate that, so please ... answers 


harisund, thanks you. very usefull :) 

I ow you a **coffe** ;)

THNX 

mods .. Im sorry.. if U find that this ofensive pls delete it....
 
-----------------------------------------------------------
*wish I had knowledge to share my time :D *

---

### Post by harisund on 2006-01-12
hbush, in another post where the parent posted had a similar problem, I had written a complete explanation. You might want to have a look at it .. 

[http://harisund-linux.blogspot.com/2006/01/uninstalling-software.html](http://harisund-linux.blogspot.com/2006/01/uninstalling-software.html)

---

