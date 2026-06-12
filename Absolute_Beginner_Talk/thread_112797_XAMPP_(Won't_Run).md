---
title: "XAMPP (Won't Run)"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-05
All website guru's outhere,

I want to learn PHP and talked to some friends about it. I knew I had to have a server/website to test what I wanted to learn but didn't know how to do it. The friends told me to use ubuntu's apt-get to set up LAMP. I tried it in ubuntu but I don't kown if it worked or not. I know I downloaded a bunch of php, apache, and mySQL packages from synaptic and installed them.
That's when I ran across XAMPP. I thought it was a good idea to try it since it came with everything already configured. I downloaded it and installed it. I tell it to start but cannot access the startpage. 
When I start XAMPP, I get: 

jaygo333@Ubuntu:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.0...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
jaygo333@Ubuntu:~$

It says there is another deamon(?) runnning but I don't know what it is.The website said that when starting, it should look like:

Starting XAMPP for Linux 1.4.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

(even though it says different version number,still same for all)
I don't know why mine is different. I try to open the default page
([http://www.apachefriends.org/images/380.jpg](http://www.apachefriends.org/images/380.jpg)) to see if it is working but get:
([http://img301.imageshack.us/img301/4002/screenshot6yy1.jpg](http://img301.imageshack.us/img301/4002/screenshot6yy1.jpg))
Mine doesn't look exactly like what its supposed to look like.
What did I do wrong. I followed all examples mentioned at the main site
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
and at the IBM Site
[http://www-128.ibm.com/developerworks/linux/library/l-xampp/](http://www-128.ibm.com/developerworks/linux/library/l-xampp/)
but still get the error. What did I do wrong.Both websites say I did it correctly and I followed all examples shown. 

Any Help Greatly Appreciated.1?1

:confused:h34r: Jaygo333 :confused:h34r:

P.S. I still don't know what that deamon(?) part meant. I know it has a great deal to do with this.

---

### Post by DoorGunner on 2006-01-05
you dont have appache already installed do you??

---

### Post by Jaygo333 on 2006-01-05
[QUOTE=DoorGunner]you dont have appache already installed do you??[/QUOTE]

I don't know.1?1
How do I check and most importantly remove it or customize it for XAMPP.1?1

:still:confused:h34r: Jaygo333 :still:confused:h34r:

---

### Post by darckhart on 2006-01-05
hi. i think you just need to check through your synaptic package manager and see what's installed. you can also goto the system menu and look for the one called services to see what services (like apache, mysql, and ftp) are running. if they are, just uninstall them from synaptic.

and i think a daemon just means a "system process" that runs at startup.

actually maybe we can help each other out later on too, cuz i want to install the webserver junk to learn ruby.

---

### Post by Jaygo333 on 2006-01-05
[QUOTE=darckhart]hi. i think you just need to check through your synaptic package manager and see what's installed. you can also goto the system menu and look for the one called services to see what services (like apache, mysql, and ftp) are running. if they are, just uninstall them from synaptic.

and i think a daemon just means a "system process" that runs at startup.

actually maybe we can help each other out later on too, cuz i want to install the webserver junk to learn ruby.[/QUOTE]

Sweet. Thanks for the advice. What do you mean when you say, 
"goto the system menu and look for the one called services" 
How do I do it. Explain more.
I'll be waiting later when you start your webserver. I'll help, 
Only if I get this thing fixed though :D

:):h34r: Jaygo333 :):h34r:

---

### Post by Cliff76 on 2006-01-06
Jaygo,

What he means is goto your system settings panel(under the Gnome or KDE menu (I almost forgot, I'm running KDE and you're probably using Gnome) and look for the system services option. I'm not sure where it is on Gnome but it's most likely under the system menu. What's happening is you already have these "daemon" services installed and running so there's a conflict. I'm not sure if XAMPP can work when the services are already up and running (I bet it could) so I suggest you check the XAMPP docs for that. I never used the XAMPP product so I can't be of much help there but I can help you understand the mechanics a little. It's a bad Idea to uninstall services like apache and mysql just to get them to not run because you don't know what other apps could be using them. On a vanilla (new) system you would probably be safe doing this but there's a better way. You probably just need to stop the services and you should be able to do that from the services panel as mentioned earlier. From my understanding LAMP or XAMPP is a product geared towards users and systems that aren't already running these services and don't want to go through the hassls of configuring them. Once again the docs for the product should give you a little more insight on what to do when you already have the services up and running.

---

### Post by darckhart on 2006-01-07
hi jaygo

sorry about the lateness. i get home pretty late from work and am too tired to do anything but eat and sleep.

ya, like what cliff said, what i meant is to check under system, administration, services menu up there in the left. another easy way to check is to open a terminal and do 'netstat --inet -a' to list all the active tcp connections. if apache is running you should see local address listening on port 80 and i think mysql is 3306.

uninstall the current ones or not is up to you. like cliff says, you mite have some other programs already depending on them, but i think synaptic will tell you if you do. gl.

---

### Post by ounas on 2006-01-07
A Deamon is ..

[COLOR="Blue"]A program that runs unattended to perform continuous or periodic systemwide functions, such as network control[/COLOR]

By the way, be carefull of Xampp can be insecure..

-Ounas :cool:

---

### Post by ukripper on 2007-05-23
> **Jaygo333 said:**
> All website guru's outhere,

I want to learn PHP and talked to some friends about it. I knew I had to have a server/website to test what I wanted to learn but didn't know how to do it. The friends told me to use ubuntu's apt-get to set up LAMP. I tried it in ubuntu but I don't kown if it worked or not. I know I downloaded a bunch of php, apache, and mySQL packages from synaptic and installed them.
That's when I ran across XAMPP. I thought it was a good idea to try it since it came with everything already configured. I downloaded it and installed it. I tell it to start but cannot access the startpage. 
When I start XAMPP, I get: 

jaygo333@Ubuntu:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.5.0...
XAMPP: Another web server daemon is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
jaygo333@Ubuntu:~$

It says there is another deamon(?) runnning but I don't know what it is.The website said that when starting, it should look like:

Starting XAMPP for Linux 1.4.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

(even though it says different version number,still same for all)
I don't know why mine is different. I try to open the default page
([http://www.apachefriends.org/images/380.jpg](http://www.apachefriends.org/images/380.jpg)) to see if it is working but get:
([http://img301.imageshack.us/img301/4002/screenshot6yy1.jpg](http://img301.imageshack.us/img301/4002/screenshot6yy1.jpg))
Mine doesn't look exactly like what its supposed to look like.
What did I do wrong. I followed all examples mentioned at the main site
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
and at the IBM Site
[http://www-128.ibm.com/developerworks/linux/library/l-xampp/](http://www-128.ibm.com/developerworks/linux/library/l-xampp/)
but still get the error. What did I do wrong.Both websites say I did it correctly and I followed all examples shown. 

Any Help Greatly Appreciated.1?1

:confused:h34r: Jaygo333 :confused:h34r:

P.S. I still don't know what that deamon(?) part meant. I know it has a great deal to do with this.

If you open up Synaptic and type Apache in search, when apache shows up, right click on each Apache marked entry and select option Mark for removal (Make sure you only mark apache1.3 ). once removed apache go to terminal and type [PHP] sudo /opt/lampp/lampp start[/PHP] and you are ready to go in firefox type [http://localhost](http://localhost)

try it:)

---

### Post by az on 2007-05-23
No.  You already have a perfectly fine LAMP stack running.  One that wil be easy to maintain.  Get rid of Xammp.

To see that the LAMP stack you installed through the package manager is running, browse localhost

Type "localhost" in your browser bar, or your IP address.

---

### Post by ukripper on 2007-05-24
To the problem, XAMPP (Won't Run).
Solution: If you want to run XAMPP remove previous LAMP stack from synaptic including Apache and stop services. Then start XAMP again.

XAMPP is easy to run and maintain also to upgrade when new versions comes in : Thanks to Apache friends.

---

