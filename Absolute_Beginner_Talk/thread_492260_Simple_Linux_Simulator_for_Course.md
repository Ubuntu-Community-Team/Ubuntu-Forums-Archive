---
title: "Simple Linux Simulator for Course"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by drakeseagles on 2007-07-04
I need a simple simulator that I can use for a UNIX college course.  The Gnoppix cd they gave me will not run on my PC.  I also tried dowloading and running Feisty Fawn and got a bunch of errors like "Buffer i/o error on device fd0, logical block 0" and some errors about squashes, etc.

I have Win XP on my PC and do not want to install another OS, or create a dual-boot system.  I just want a simulator where I can run the commands for the labs,  record the result (by which I assume they mean screen print) and access the Internet to post the file to the class forum.

Is there something that will work this way?  I thought I saw something like that with the Badger version, but now I cant find the page again.

---

### Post by Golyadkin on 2007-07-04
Well, you just need to download and boot from the Feisty Fawn live-cd. The fd0 error is a known bug for some people, and there is a fix for it somewhere here on the forums. I am sure you can find it using the search, or maybe someone who knows will tell you.

---

### Post by Nikron on 2007-07-04
You can try dedicated cds like knoppix or puppy

---

### Post by haricharan on 2007-07-04
if you just want to run on Windoze u can use cygwin [http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by nitro_n2o on 2007-07-04
Try [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)  you can boot it from a flash thumb drive if your motherboard supports that

---

### Post by drakeseagles on 2007-07-04
> **haricharan said:**
> if you just want to run on Windoze u can use cygwin [http://www.cygwin.com/](http://www.cygwin.com/)

Cygwin installed quickly and easily and looked like just what I need, but when I tried to do my first lab, it does not recognize commands like man adduser or adduser.

---

### Post by robertc36 on 2007-07-04
You could also try this [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Qrk on 2007-07-04
Why don't you try SLAX, using the copy2ram bootcode? It has a nice KDE gui and will load into RAM from a cd. 

[www.slax.org](www.slax.org)

Its a very nice liveCD, one of my favorites. The only downside is that it doesn't seem to support as much hardware as ubuntu, particularly wireless cards.

---

### Post by steve.horsley on 2007-07-04
Another possibility is to use either VMware or VirtualBox (both have free versions) and run a Linux version of your choice inside a virtual machine. This gives you a full Linux installation and hides it from any difficulties with any problematic hardware that might be causing your problems with live CDs.

---

### Post by dbott67 on 2007-07-04
> **steve.horsley said:**
> Another possibility is to use either VMware or VirtualBox (both have free versions) and run a Linux version of your choice inside a virtual machine. This gives you a full Linux installation and hides it from any difficulties with any problematic hardware that might be causing your problems with live CDs.

+1

This would be your best option if your computer has a decent amount of RAM (512 MB or more), CPU power (1.8 GHz+) & free hard drive space (at least 3 or 4 GB to create the virtual hard drive).

I run VMWare on my 1.8 GHz computer with 384 MB RAM and a 30 GB hard drive.  Works like a charm!

-Dave

---

