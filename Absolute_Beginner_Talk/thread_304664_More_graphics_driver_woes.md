---
title: "More graphics driver woes"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by John E on 2006-11-22
5 days have now passed but I STILL haven't managed to get my monitor to display anything higher than 640 x 480.

Acting on advice received yesterday, I went to the Matrox web site and downloaded the latest drivers for my graphics card (a Matrox G400 dual-head). The file was named **matrox_driver-x86_32-4.4.0.tar.gz**. The first problem was where to put the tar file. The Readme file doesn't give any clues - so I put it into /etc - which seemed as good a place as any. After half an hour of messing around with command lines, I finally managed to get it to unpack. The drivers seemed to extract to a folder under /etc called **matrox_driver-x86_32-4.4.0**.

At this point, the instructions told me to change to the folder called **mga_drivers** where I'd find a file called **Install.sh**. However, no such folder exists. There is such a file in **matrox_driver-x86_32-4.4.0** so I changed to that folder instead.

The next step was to run this command:- **sh install.sh** but when I do that, I receive a message saying **ERROR: Cannot find the X Server driver install path.**
I suppose that means something to somebody. Unfortunately, it means nothing at all to me. Can anyone please tell me what might be wrong?

---

### Post by steven8 on 2006-11-22
I am not the best to help, but I recently found out about 'hidden folders'.  Go to your home folder, and hit ctrl-h.  This shows you the hidden folders, where you amy find the mga_drivers folder.  Then you can figure out the path to run install.h.

---

### Post by steve.horsley on 2006-11-22
I used to run a Matrox G400, and the driver was always built into Linux. I wish I could remember the name of the driver. 

Have you tried the command:
**sudo dpkg-reconfigure xserver-xorg**
which will ask you about the resolutions you want (along with lots of other questions)? Make a backup copy of the file /etc/X11/xorg.conf first so that you can put it back if the reconfiguration goes really wrong. This is the approach that is normally recommended for fixing screen resolutions. Just take the default answer for any questions you don't know the answer to.

---

### Post by judgejudy on 2006-11-22
try this howto

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by John E on 2006-11-22
Thanks guys. Steve, when I tried your suggestion I got the error:- **Conflicting actions --control and --remove**

If I type this:- **sudo dpkg --configure xserver-xorg** I get the message:- **XServer is already installed and configured**

---

### Post by John E on 2006-11-22
Can anyone help with this? To re-cap - when I try to install drivers for my graphics card I get an error saying it can't find the XServer install path. However, if I try to re-configure manually, I get the errors shown in the above post.

---

### Post by Bachstelze on 2006-11-22
It's "reconfigure", not "configure" and with only one dash (-) ;)

---

### Post by John E on 2006-11-22
I've tried both. When I use **-reconfigure** I get the message about **Conflicting actions --control and --remove**

---

### Post by steve.horsley on 2006-11-22
I think it should be **dpkg-reconfigure** as one word without spaces, and **xserver-xorg** also as one word without spaces. so there are only two spaces in the whole command:
**sudo dpkg-reconfigure xserver-xorg**

---

### Post by John E on 2006-11-22
Thanks again, Steve. I'm pretty sure I tried that variation first -  but I'll try it again and let you know the outcome.

---

### Post by John E on 2006-11-22
Woohoo...! Thanks Steve, you've saved my life again.... I'm certain I'd already tried that configuration but this time it's worked. Finally (after 5 days!) I can see my desktop at 1600x1200 resolution, which I thought would never happen.

I still need to get the right-hand monitor to work (as it happens, I've got a dual-head display) but that can wait until tomorrow. Thanks, once again.

---

