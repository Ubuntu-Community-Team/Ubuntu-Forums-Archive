---
title: "Booting from External Harddrive"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by krispykreme on 2007-02-21
I just got Ubuntu installed onto my External Harddrive. Now I just need to find out how to boot my computer from it.

---

### Post by Zuuswa on 2007-02-21
Go into your BIOS settings.  If it allows you to boot from external devices (i.e. usb), then you should be all set.

---

### Post by krispykreme on 2007-02-21
I went into my Bios and choose USB-HDD and it still booted to Windows. I might not have installed Linux right. All I did was get the Ubuntu CD in the mail, load the live CD and had the installer partition and install. Is there more I need to do before it will work?

---

### Post by yanqui on 2007-02-21
You probably installed it just fine, but booting from an external hard drive requires a little more work.  The thread below takes you through a great process, in fact you may becide to start all over.  I used the live version and got it installed on the usb hard drive but was never able to get it to boot even using these instructions.  I downloaded the "alternate" version and it worked fine.  Couple of additional things not mentioned in the instructions--type everything exactly!  Also, the instructions were for something slightly different so what he says you should see you may not see exactly, but you will know that it's going correctly.  Another thing--my computer holds the recognition in bios of the external usb hard drive--for as long as the drive is physically connected.  If I disconnect the drive from the computer, I have to go back into bios and reselect the usbconnected drive to boot before the internal hard drive.  This process does NOT work with live versions--I've also tried it with Mepis, which is a live distribution, and it did not work.  You are certainly welcome to try it, you may get it to work.  This process described below will show you how to load support for USB before the whole drive is loaded, so that the drive will mount; or something like that.  It will also advise you to put the GRUB onto the external drive rather than the internal drive; the purpose behind that is that if the external drive is not connected, GRUB won't know quite what to do if the grub is loaded to the mbr of the internal drive.

Good luck, and let us know how it went.


[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

---

