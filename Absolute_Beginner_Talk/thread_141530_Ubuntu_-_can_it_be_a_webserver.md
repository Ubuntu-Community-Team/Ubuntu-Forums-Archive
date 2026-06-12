---
title: "Ubuntu - can it be a webserver?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-08
Hey,

I'm new to Linux and Ubuntu but not new to programing or webhosting.

My question is this:
Can I use the Ubuntu release of Linux on an Intel P3 to function as a webserver for roughly ten sites?

I've looked at fedora, debian and others but I'm still not sure if I need a server version of Linux or if a desktop version (I think that's what's in the download area...?) will do the trick.

All help is greatly appreciated!

gs

---

### Post by soce_32 on 2006-03-08
Yes.  Ubuntu has Apache, Zope, Tomcat and several other web servers in the repositories.

---

### Post by guysmiley on 2006-03-08
Thanks Soce!

I promise not to bug you again, but can you tell me where to find a list of what the Ubuntu bundle contains (i.e other than FF and Open Office)?  I'm specifically wondering if there's an ftp server, php, apache, mysql bundled...

gs

---

### Post by psusi on 2006-03-08
Fire up synaptic and search for packages, or you can search at [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by LordBug on 2006-03-08
I setup Apache, PHP, and MySQL on a test Ubuntu system once, to see how it went.  Took a few hours to get it all working correctly, but it's not too bad.  All the installations you'll need are in the repositories.  There's no bundles like you're looking for though.  You'll have to grab Apache, PHP, MySQL, and the FTP server you want individually.  This will allow you to setup the versions you want.  I know Apache 1 and 2 and PHP 4 and 5 are in the repositories, so take your pick on what you want.

You'll have to spend some with the config files to tweak Apache the way you need, and learn the appropriate MySQL commands to get account on it up and running.  After that, it should all hum along nicely.

---

### Post by WelterPelter on 2006-03-08
Also, you should be able to query these forums and find threads containing all (or at least a lot of) the guidance you need to set this stuff up.

---

### Post by eltaito on 2006-03-08
yeah these forums are great for virutally ANYTHING you need to know about Ubuntu....great community.  I run Apache2, with MySQL, PHP...etc on a home box with no problems.......I am running it with XFCE because I am new to the whole "server" thing and running a server box from just command line was kinda scary.  And if you are looking for a good FTP server, I am using ProFTP and have had no problems with it yet.  It would be a perfect setup if my ISP didn't strangle my upload bandwidth.....stupid TimeWarner

---

