---
title: "machine would not boot via grub - 1st April?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by darkworld on 2008-04-01
Have had no problems at all until today, 1st of April, machine boots straight onto windows drive and doesnt appear to run grub off Ubuntu drive. Windows XP then doesnt manage to completely boot. 

I have two sata drives, Ubuntu installed separate and windows installed separately, so I think there are two MBR's because of how I did the installation months ago, unplugged opposite sata drive when installing each OS.

 Ive checked grub menu.lst and that looks fine. I had to select to boot Ubuntu drive via bios drive boot selection (Esc during post), then grub came up and I booted Ubuntu.

If I leave machine to just boot it ignores Ubuntu drive, doesnt give grub option - Ubuntu is default drive normally, and goes straight to what appears now to be a virus hit windows. Im only guessing its a virus because its April the 1st

Can anybody advise me? My setup has not been any problem until this morning.

---

### Post by Xiong Chiamiov on 2008-04-01
If indeed it is a virus that has affected your Windows installation, it sounds to me like it rewrote part of your MBR.  You may want to try putting grub [back into the MBR]("http://ubuntuforums.org/archive/index.php/t-24113.html") on your primary drive.

---

### Post by darkworld on 2008-04-01
Thanks for the advice but im not sure thats the problem. 

Its like after post screen it goes to look for MBR and skips my Unbuntu MBR and goes straight to windows drive MBR. Is that a BIOS issue? Ubuntu on sata channel 2 and Xp on sata channel 3. I thought it just polled the sata channels in sequence looking for MBR and would always find Ubuntu MBR first where grub resides.

If I boot my PC then press ESC during post the Bios calls up both hard drives in a menu where I can select which on I want to boot from, when I do it like this I select the Ubuntu sata drive and it then finds MBR and fires up grub menu.

I think I need to work out why for some reason its decided to skip the Ubuntu MBR when booting unassisted????

---

### Post by darkworld on 2008-04-01
Now im bugged!

Ive just reinstalled Grub and the problem remains!

/dev/sda2 /boot

grub

root (hd0,1)

setup (hd0,1)

does the reinstall then I quit and restart......straight into windows drive! aaaaaaargh!

---

### Post by udh on 2008-04-01
> **darkworld said:**
> Now im bugged!

Ive just reinstalled Grub and the problem remains!

/dev/sda2 /boot

grub

root (hd0,1)

setup (hd0,1)

does the reinstall then I quit and restart......straight into windows drive! aaaaaaargh!


**this might help, have a look: **

> **[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)**

---

### Post by darkworld on 2008-04-02
I found it! 

The hard drive boot priority had changed in the BIOS (on the 1st of April.) 

 My BIOS is passworded. 

My family have access to machine. They do not have access to BIOS. How can this of occurred? I have not been into BIOS myself.

---

