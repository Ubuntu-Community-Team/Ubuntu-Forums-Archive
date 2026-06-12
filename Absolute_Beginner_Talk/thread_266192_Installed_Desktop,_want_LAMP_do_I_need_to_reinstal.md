---
title: "Installed Desktop, want LAMP do I need to reinstall using Server?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by ptejada on 2006-09-26
I am new to Ubuntu and I want to create a simple website to host photo albums (Coppermine).  I would prefer to install a LAMP stack quickly, is there an equivalent to apt-get install Ubuntu-desktop that will install the LAMP stack?  Is there a tutorial or am I better served by reinstalling using server and adding the desktop?  I want to use the PC for both the website and general web surfing.

Thanks in advance.  :D 

-Pablo

---

### Post by Mr Frosti on 2006-09-26
There is not a LAMP metapackage that I know of. You can however, very quickly install the missing components without having to reload server edition.

From a terminal, type in "sudo apt-get install apache php mysql"

This will install the missing packages and their dependencies. The trickiest part will be modifying the configuration files to get your environment setup.

---

### Post by bodhi.zazen on 2006-09-27
[[color=blue]How to Ubuntu LAMP[/color]](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by DarkKoopa on 2006-09-27
If you decide to reinstall from scratch (which I did was it was the quickest and easiest way for me being a n00b).....

I installed the Ubuntu LAMP server from the sperate iso, and then used this guide

[http://www.howtoforge.com/node/1388](http://www.howtoforge.com/node/1388)

to install the GNOME GUI.

I didn't have to reconfigure anything that this tutorial goes on about in the latter pages with using WebMin (as I didn't install it).... All I did was install LAMP, install GUI and then FTP'd Wordpress into the /var/www/ folder.

I then downloaded PHPMyAdmin and created a user for SQL and 

BAM

Worked first shot.

Took no more than 90 minutes.

---

