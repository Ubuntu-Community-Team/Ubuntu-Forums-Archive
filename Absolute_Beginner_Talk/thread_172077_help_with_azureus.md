---
title: "help with azureus"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-05-07
hi, I recently installed azureus version 2.4.0.2. when i atempted to start a torrent it said that the client was not allowed on the site, i contacted the admin of the tracker and i was told, "The problem is that your java is out of date, which causes problems with Azureus on Linux. You need to upgrade your JRE to the latest version and edit Azureus' startup script to point to the new java. You need to do this before you use any torrents here again, or your account may be disabled." i installed the latest version of JRE, but i don't know how to edit Azureus' startup script to point to the new java. does anyone know how to do this?

Much thanks,
cptjaben

---

### Post by nalmeth on 2006-05-07
this should be done automatically, but I find it odd that you've encountered this.
Ubuntu offer's the free, reduced Java Blackdown (1.4) to run azureus and other java based apps. I'm suprised you've been told to get better java.
You might try uninstalling java, purging config files, and reinstalling it:
sudo apt-get --purge remove azureus

don't know what else to say really!

---

### Post by tenn on 2006-05-07
Once the Java 1.5 is installed if you do this, 
"sudo update-alternatives --config java" in terminal and select java 1.5 and start Azureus it should than use Java 1.5.

---

### Post by cptjaben on 2006-05-07
Thanks much for the help.

---

