---
title: "bcm43xx-fwcutter problems"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by boomcat on 2007-08-11
I'm trying to install Automatix and the installation fails with an error message: 
"error processing bcm43xx-fwcutter"

The name bcm43xx-fwcutter sounds like a file that I was trying to install a few days ago to make my Linksys wireless card work. I had a dozen failed attempts before I finally got the card working. Maybe this file is some sort of a vestige of those failed installs.

How can I clean this up? It's interfering with all of my installs.

---

### Post by kevin11951 on 2007-08-11
wut the hell is 43xx blah da blah blah?!

---

### Post by mattman85 on 2007-11-22
I'm running 7.04 AMD64-bit..


the error that I get with BCM43XX-FWCUTTER is the following:
matthew@matthew-lt:~/Desktop/bcm43xx-fwcutter-006$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.6kB of archives.
After unpacking 123kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 102840 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_amd64.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--11:14:04--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:14:05 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)


And every time i try to do something, almost anything, it yells about bcm43xx-fwcutter not working right..  what should I do?

---

### Post by phil.munck on 2008-02-13
I'd like to join in with this.  
I abandoned my attempts to get a Linksys WPC54G v. 3 card to work after trying many approaches - some of which involved fwcutter.  The problem seems to be a script that invokes a link to [http://boredlink.googlepages.com/wl_apsta.o](http://boredlink.googlepages.com/wl_apsta.o) which no longer exists.  
Since then, every package I install seems to return a p

"E:bcm43xx-fwcutter: subprocess post-installation script returned exit status 1"

or something similar.  I also am unable to install Automatix because of this problem.

Is there a root uninstallation that would get me back to ground zero short of reinstalling 7.04?

---

