---
title: "iMac G4 Boot Problems"
date: 2011-08-09
forum: Apple Hardware Users
---

### Post by chrisduds on 2011-08-09
Hi,
I'm using an old iMac G4 and would like to install Ubuntu 10.10 (Power PC Architecture.) When I try to boot from the CD by holding down the C key, the computer screen stays gray for about 20 seconds and then spits out the disk. I've tried using the F10 key but that doesn't work either. My iMac can play regular CDs and DVDs fine. Please give some suggestions. Thanks!

---

### Post by rsavage on 2011-08-10
Maybe there has been a problem with the burn?  Do you hear it tryng to read the disk?  Did you do it on the lowest speed?  You could give the alternate CD a go?  If you have a spare/empty usb stick then you can boot from that instead.  It is the way I boot everything now.  There are instructions on the forum.

---

### Post by chrisduds on 2011-08-10
I've tried burning Ubuntu several times but I've never tried burning it on a lower speed (I'll try that.) I do here it trying to read the disc in Mac OS X but it takes the computer a few minutes before it shows the disc. As a last resort I'll try USB but it is difficult to do it on a Mac.

---

### Post by chrisduds on 2011-08-10
I tried burning it on a lower speed but it still doesn't work. I need some help creating the .img file on a Mac for the thumb drive (according to Ubuntu's instructions). Please be really specific.

---

### Post by rsavage on 2011-08-10
Is this any help [http://ubuntuforums.org/archive/index.php/t-1445659.html](http://ubuntuforums.org/archive/index.php/t-1445659.html) ?
 
From post 38 on here [http://ubuntuforums.org/showthread.php?t=780320&page=4](http://ubuntuforums.org/showthread.php?t=780320&page=4) .

---

### Post by linuxopjemac on 2011-08-10
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by chrisduds on 2011-08-10
I've burned several ISO discs and they boot fine on my other computers. And I've als tried to make a USB stick but when I try to convert the ISO to IMG I get this: 
```
hdiutil convert -format <format> -o <outfile> [options] <image>
hdiutil convert -help
```

---

### Post by chrisduds on 2011-08-10
Well, I converted the newest version of Linux with success. My only problem is whether it will work on a Powerpc. If you can forward me to something about Powerpc processors and Linux I'd really appreciate it.

---

### Post by rsavage on 2011-08-11
I'm a little confused now what you have downloaded/burned/converted.  The power pc iso's are here [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) .  Note, 10.10 says it won't fit on a standard CD so is this your problem with the burning?
 
The latest version of Ubuntu is 11.04 although I'd be surprised if you found an iso for powerpc.  You may find an iso for 11.10 but that is in development. See the powerpc sticky for ways to install 11.04.

---

### Post by chrisduds on 2011-08-11
I'm using a DVD for all my ISOs. I can burn working ISOs from the newest Intel ISOs and convert them for use on a flash drive. The PowerPC ISOs I can't seem to burn correctly or convert for use on a flash drive.

---

### Post by rsavage on 2011-08-11
What about running ubuntu (live cd or installed) on one of your intel machines and copying the powerpc iso on to usb from there?  Linuxopjemac will tell you it doesn't work, but I can't see why not personally.  The dd command just copies raw data afterall.  See my posts on the link I gave you earlier for instructions.  
 
Have you checked the checksums for the iso like on the other links? 
 
Sorry, can't be much more help.  Have never used a mac os!

---

