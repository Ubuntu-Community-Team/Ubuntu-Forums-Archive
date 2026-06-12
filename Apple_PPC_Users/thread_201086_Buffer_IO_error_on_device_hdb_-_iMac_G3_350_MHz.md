---
title: "Buffer I/O error on device hdb - iMac G3 350 MHz"
date: 2006-06-21
forum: Apple PPC Users
---

### Post by Henke on 2006-06-21
I'm trying to install 6.06 on my iMac G3 350 MHz. When i boot on the CD it runs pretty well the first minute, but when it reaches the "Creating LIVE user", or something like that the cd-player starts sounding weird and after a while I get this message:

[189.300267] Buffer I/O error on device hdb, logical block 39550
[199.303260] Buffer I/O error on device hdb, logical block 39551

and so the computer goes on and on... I have burned the latest ISO-file in 4x, so I think the cd should work properly!

How do I deal with this?
Henrik

---

### Post by bigfox on 2006-06-22
I have a similar issue on my old iBook G3 300Mhz (Blue armored clamshell)

I think it is the very old drive just crapping out.  It has issues reading burned disks no mater how slow the burn, but read pressed disks better.

If your CD drive is original, it may just be showing its age like mine is.

---

### Post by Henke on 2006-06-22
But why has the drive problem with just this cd? Yesterday I tried my old 5.10-cd with no problems (exept that the installation stops at "enter previous installed session"...) :(

---

### Post by sean talbert on 2006-06-23
I'm getting the same issue installing to a Dell Optiplex with an Ubunto Desktop CD that I burned from an ISO image.

Here's the interesting part... the Ubuntu Server CD, also burned from an ISO image works on the same computer, and the Ubuntu Desktop CD works on a different computer.

Still looking around for a reason why... found an answer to my problem in the 'Installer stalls at "mounting root file system"' thread... added "irqpoll" to the boot options and it got past the "Buffer I/O error on device hdc, logical block..." errors to the install.

---

### Post by warp99 on 2006-06-23
Problem is that most of the older drives were produced before ISO yellow book CDR was available, so some burns will work while others will not. :( 

The 300mhz clamshell I have wouldn't read burned discs with the original CD-Rom, so I updated to a CD-DVD for about $20 USD. You can pick a replacement drive used or even new dirt cheap. Macs just have a standard IDE optical drive, nothing fancy. :cool:

---

### Post by dozch on 2006-09-11
I had the same buffer I/O problems on my freebie BlueBerry iMac but in the end I did get Xubuntu installed. After creating enough coasters for an average diner party, I burned a Xubuntu-alternate 6.06.1 image at 2x speed with CDBurnerXP 3.0.116 on windoze that worked. For some reason, K3B wouldn't burn at a lower speed than 4x... 

Xubuntu works quite well on this low end Mac - a great way to spice up an old iMac!

---

### Post by nadamsieee on 2006-10-23
[http://ubuntuforums.org/showthread.php?p=1653875](http://ubuntuforums.org/showthread.php?p=1653875)

---

