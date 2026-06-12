---
title: "Xubuntu Gutsy iMac question"
date: 2007-11-30
forum: Apple PPC Users
---

### Post by docinsano on 2007-11-30
Well, I think my old iMac was a little too old to run Ubuntu so I switched over to Xubuntu. Ahh, now it works much better. Just a quick question: what do I need to do to get the modprobe ide-core thing to run when i boot so i don't have to wait for the busybox prompt every time I boot. That is all. 

Later

The Doc

---

### Post by crc7173 on 2007-12-04
Yesterday I installed Ubuntu on a 400Mhz iMac Slot Loader by following most of the steps I found here: 
[http://ph.ubuntuforums.com/showthread.php?t=615089]("http://ph.ubuntuforums.com/showthread.php?t=615089 ")

Specifically, I think lines 16-18 will help it play nice on boot:

[B]sudo nano /etc/initramfs-tools/modules
[/B]add the line** ide_core** and **ide_disk** (ctrl + x, press y, press enter to save) 
** sudo reboot**

I'm guessing the same steps will apply to Xubuntu as well.

---

### Post by dvenardos on 2007-12-05
> **docinsano said:**
> Well, I think my old iMac was a little too old to run Ubuntu so I switched over to Xubuntu.  Would you post your xorg.conf to this post? I can't get the XServer running on my iMac G3:
[http://ubuntuforums.org/showthread.php?t=630033](http://ubuntuforums.org/showthread.php?t=630033)

---

