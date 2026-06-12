---
title: "window manager not responding"
date: 2011-09-06
forum: Apple Hardware Users
---

### Post by drgnswrd on 2011-09-06
I'm running Ubuntu 11.04 on an iBook G4 (1.2GHz powerpc processor, 1.2 GB ram).  To be honest, it runs slower than the machine did with OSX 10.5.8, but it does what it need it to do (media server, running MediaTomb).  Since the last major update a few days ago, it's worse than usual.  I can't even get file manager windows to load.  If I do places/downloads, it takes about 5 minutes to start drawing the window, but never gets farther than the white box and title bar.  If I double click on the icons for any of the external drives, it doesn't do anything at all.  I usually control it remotely with screen sharing from my MacBook pro.  When I "connect to server" and map to the drives, It performs as fast as you could want.  The screen sharing has always had a delay.  I have no idea where to even start.  I've tried killing unnecessary processes, I've tried restarting, and shutting down and leaving it off for a while then booting.  I have no idea where else to check.  I'd just be happy for it to draw the windows again.  Any ideas?

---

### Post by rsavage on 2011-09-07
Have you tried it without the  apt-xapian-index package?  That used to cause me lock ups.  Software centre and update manager run an million times better without it.

The only other thing I can think of is to make sure you have the optimum settings in your xorg.conf file.  For example, have you got the gart size set to 16? 

I have the same model of ibook as you (only with far less ram) and gave up on standard ubuntu at 11.04.  However, 11.04 Xubuntu and Lubuntu are a joy to use on that computer.

---

### Post by drgnswrd on 2011-09-12
> **rsavage said:**
> Have you tried it without the  apt-xapian-index package?  That used to cause me lock ups.  Software centre and update manager run an million times better without it.

The only other thing I can think of is to make sure you have the optimum settings in your xorg.conf file.  For example, have you got the gart size set to 16? 

I have the same model of ibook as you (only with far less ram) and gave up on standard ubuntu at 11.04.  However, 11.04 Xubuntu and Lubuntu are a joy to use on that computer.

I'll try killing apt-xapian-index, and see if I can tweek xorg.conf.  i may try Xubuntu or Lubuntu later.  

Thanks for the ideas.

---

### Post by rsavage on 2011-09-12
Just in case you haven't seen [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) .  Post 7 for xubuntu.

---

### Post by svtguy88 on 2011-09-13
I would try the Lubuntu.  The latest Live CD I tried installs on my Powerbook with minimal tweaking (I had to log in, and type "startx" ...big deal).  It also seems to have good control over the nouveau driver for nVidia graphics (assuming you have this, and not an ATI chip).  My G4 has an nVidia card, and even with a dual 1.8 ghz upgrade, a bad video driver taxes the CPU hard when doing even basic GUI functions.  

I guess my question would be what kind of GPU do you have in you machine?

---

### Post by drgnswrd on 2011-09-17
> **rsavage said:**
> Just in case you haven't seen [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) .  Post 7 for xubuntu.

Thanks for the link.  It might work.  I'll look through it and give it a try.  I did notice Xubuntu and Lubuntu didn't have ppc versions already compiled.

---

### Post by svtguy88 on 2011-09-17
There is a Live CD for Lubuntu, but it's still in the beta stage.  It is version 11.10, and the daily builds can be downloaded [here.]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by drgnswrd on 2011-09-19
> **rsavage said:**
> Just in case you haven't seen [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792) .  Post 7 for xubuntu.

Xubuntu is installed and running.  Mediatomb is installed and running.  Computer is still responding to me as fast as I could want.  working on getting remote desktop up and running so I can leave it sitting on top of the TV case with the external drives plugged in and control it from my other laptop.  So far, I'm thrilled.  Thank you for the help.

---

