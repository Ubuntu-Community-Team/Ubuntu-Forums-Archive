---
title: "Linux inside Windows using its own partition which already has an installation of..."
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by Aiden on 2005-12-12
Linux inside Windows using its own partition which already has an installation of Ubunty on it usint EXT3 filesystem. Is this possible?

Basically, I want to be able to run Ubuntu inside windows but have everything read from the partition that it is currently installed to, so no VMware or VirtualPC as those create images to use to boot from (to my knowledge). I just want to be able to work on linux inside Windows and hopefully in a week or two Ill be able to go to Ubuntu full time instead of dual booting.

---

### Post by kingsidy on 2005-12-12
I think that you have to use one of those virtual programs to run linux within windows. Although i have heard of Colinux, which allows you to run linux in windows i think. I am not oo sure though. But u can google it and see.

---

### Post by aysiu on 2005-12-12
Damn Small Linux has an embedded version you can run inside Windows, but the files are stored on Windows (not a separate partition), and... it's damn small.

---

### Post by void_false on 2005-12-12
[QUOTE=aysiu]Damn Small Linux has an embedded version you can run inside Windows, but the files are stored on Windows (not a separate partition), and... it's damn small.[/QUOTE]
Could you plz specify some links? Because I've never heard about that embedded version. :cool:

---

### Post by cwaldbieser on 2005-12-12
[QUOTE=Aiden]Linux inside Windows using its own partition which already has an installation of Ubunty on it usint EXT3 filesystem. Is this possible?

Basically, I want to be able to run Ubuntu inside windows but have everything read from the partition that it is currently installed to, so no VMware or VirtualPC as those create images to use to boot from (to my knowledge). I just want to be able to work on linux inside Windows and hopefully in a week or two Ill be able to go to Ubuntu full time instead of dual booting.[/QUOTE]
I don't know about having it run an ext3 filesystem from an NTFS or FAT32 partition-- otherwise I have seen this done with CoLinux.  If you search for TopologiLinux, they have a nice setup that is actually very usable.

---

### Post by aysiu on 2005-12-12
[QUOTE=void_false]Could you plz specify some links? Because I've never heard about that embedded version. :cool:[/QUOTE] Here's a link:
[http://dsl.thegeekery.com/current/dsl-2.0-embedded.zip](http://dsl.thegeekery.com/current/dsl-2.0-embedded.zip)

You unzip it and click on *dsl-windows.bat*

---

### Post by Chayak on 2005-12-12
You can with VMware using the advanced functions and use a physical partition instead of a virtual disk.

---

### Post by void_false on 2005-12-12
Wow great! Works brilliant. 
Although it detected my CPU as P2 instead of Athlon ;)

---

