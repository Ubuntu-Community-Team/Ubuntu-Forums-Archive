---
title: "Successful without terminal Triboot (OS X Leopard, Ubuntu 8.04 &amp;  XP SP2) on Macbook"
date: 2008-07-24
forum: Apple Hardware Users
---

### Post by Yellow-Lime on 2008-07-24
Hi there,

Linux and all is quite new to me but I thought of giving it a fair chance and  wanted it to install the latest Ubuntu distro (8.04) on my macbook (3rd gen).  Searching the web I found many different possibilities for a triple boot but actually none did the trick for me. I am quite unfamiliar with command lines (one of the reasons I wanted to try Linux to improve this skill) and I was actually trying to find a way for a triple boot without using any command line(s). And I succeeded!

The original "tutorial"  (based upon a triboot of Vista, Leopard and Ubuntu 7) was made up by some one else, also related to the Ubuntu forums. I would gladly post a link or mention the author who should get the majority of the credits but unfortunately I cant find the address anymore. However I did modify the tutorial as his was not working for me because I wanted to use XP instead of Vista.

Note* This tutorial was done with a newly installed Leopard (V# 10.5) on a **Macbook** 2GH, core 2 duo, 4GB Ram and a WD Scorpio HDD 320 Gigs 5400 RPM. 


1) I installed OS X Leopard on my internal HDD. I did a custom install (removing some printer drivers, language stuff ect.) but it should not matter! A clean install is what you need!

2) I used bootcamp to make a partition for XP (58 GB) and choose NOT to RESTART but choose the other option of  "install later".

3) After bootcamp made the XP partition I made another partition for Ubuntu. I divided my main HDD where Leopard was installed in two. The main partition remained for Leopard and the second smaller one (70 GB) was formatted as Mac Journaled. 

4)  When I opened Bootcamp it did not allow me to reboot to the XP install CD because of the extra partition that I made for Ubuntu. I quitted Bootcamp and inserted the XP install CD and booted manually of the CD holding down the "C" key after the chime. This worked perfectly and the install CD installed XP.  

**NOTE*** The machine booted a few times during installation and due the fact that I had NOT installed Refit it booted right into OS X. What I did was every time it booted in OS X I restarted the machine  and booted of the XP install CD again holding the "C" after the chime. I think it happened about two or three times. The install just continued where it stopped when I booted of the XP CD. I have not tried this method using refit.

5) After XP was installed I inserted the Leopard install disc (Disc 1) in order to install the drivers for isight, wireless etc. 

6) After the driver install I booted in OS X to check if everything still worked and yes it did. I installed refit  and inserted the Ubuntu 8.04 live CD and restarted the machine. Refit nicely displayed the Ubuntu live CD and I choose trough refit to boot from the CD. Eventually I formated the Mac partition with the live CD to ext3 and continued the installation. Be ware that on the final install screen you choose the ADVANCED option and choose to install the boot-loader on the Ubuntu partition and not on another disk because it can overwrite the mac EFI resulting in not being able to boot in OS X anymore (or so I have been told).

After completing step 1 to 6 I was able to boot into every OS without issues! 

Good Luck!


Tools: 

-Live CD Ubuntu 8.04 (you can download it and burn it to a CD, instructions can be found on the official Ubuntu site)

-Mac OS X (Leopard) install disc 1 and or 2
-XP install disc SP2
-Refit

---

### Post by cyberdork33 on 2008-07-24
That is what I would have recommended. Create all your partitions upfront, then install Windows and you usually will have less problems.

---

### Post by kdb424 on 2008-07-24
Huge tip from what I did. While it is at the insert disk and restart screen in bootcamp, leave that open while you partition your hard drive and it will still restart and install windows the easy way, no holding C down.

---

