---
title: "My laptop won't boot anymore"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-03-24
Hi there,

3 months ago I found out about Ubuntu and then I just switched from Windows XP to Ubuntu 7.10 on a Toshiba laptop. Now I wanted to re install my Windows just to run the Adobe Photoshop that I have. So I followed a tutorial to make the computer a dual boot. Now, while Windows installed itself it reboots and then comes up with the message 

Disk error 
Press any key to restart

So, something obviously went wrong (I'm writing this from another computer), re starting the Windows install doesn't work either.

Well, I thought, not such a big deal, lets use the Ubuntu Live CD to get back into Ubuntu, change the GRUB-Loader so Ubuntu get automatically loaded when I start the computer and that'll be it for now.

When I start the computer, press F12 to enter the Boot-Menu, go to CD (with the Ubuntu 7.10 Live CD in it), the following happens:

Intel(R) Boot AGent FE v4.1.18
Copyright (C) 1997-2005, Intel Coorperation

Initializing and establishing link...




and then

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent


to be followed by

Disk error
Press any key to restart


So, i googled that up, normally it is because of a cable (which I rule out), a worn out hard drive (which I think it just as unlikly).

I think the Windows install messed up with my BIOS, but as I know nothing about it I am hesitant about messing with it.

Sorry for bothering you guys with so much Windows talk, at this point I just want my Ubuntu back, so if anybody can give me tips on how to get my old Ubuntu running (which is still on its own partition) that would be splendid

Thanks so much
Andreas

---

### Post by Dithers on 2008-03-24
have you tried super grub disk

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by Cresho on 2008-03-24
Well, When ever I reinstall my operating system, I leave home alone.  So for example, my main hardrive is 3 partitions Root (sda1), swap (sda2), home (sda3) sda is sata drive and Of course when I use the live cd, i use / for root, and /home for home.  Root gets a check for formating.I format the root partition and when it asks me for my username and password, I enter it exactly like I did the first time I installed.  when ubuntu after everything, my ubuntu boots up with all my configurations in place minus the install.  So after configuring hardware, I just install the software and my configuration is already set like my screenlets, avant window navigator, Compiz Fusion, ME-TV for HDTV and TVTime for Regular tv.  All configurations are already set, just a matter of installing what I dont have after a re-install.

Good luck.  This is just my expirience and remember to always keep a backup of your stuff!

---

### Post by Djalmahal on 2008-03-24
Hi Dithers, it's late now, I'll try if it accepts the Super Grub Tool tomorrow morning, thanks

---

