---
title: "Homemade Xubuntu CD not booting on Mac"
date: 2008-09-01
forum: Apple Hardware Users
---

### Post by BeautyandSong on 2008-09-01
Hi:

I'm trying to make a bootable Xubuntu CD on my Mac. I downloaded the Xubuntu ISO and burned it using Disk Utility, but it won't boot. I try pressing C, and pressing Apple+Opt+Shift+Del, or even pressing Option when starting up my computer and it doesn't do anything. When I use the 4key method, I can hear the CD drive working and it takes a really long time to finally boot up, I can tell it's trying to boot the CD, but it simply goes to a "Safe Boot" mode of Mac OS X. When I press the Option key it doesn't list a Xubuntu CD. When I press the C key it simply does nothing. 

I'm trying to boot the Xubuntu CD so I can follow the instructions here: [http://planet.barcamp.lv/2008/07/29/guide-how-to-install-xubintu-on-acer-aspire-one/](http://planet.barcamp.lv/2008/07/29/guide-how-to-install-xubintu-on-acer-aspire-one/) and put Xubuntu on my netbook which doesn't have a CD drive. 

I have Mac OS X 10.4.11 installed, and I'm running a 1.42 Ghz G4 PPC Mac Mini. Just an FYI: I have an old Ubuntu 6 for PPC CD and tried to boot it just to see if it's a problem with my hardware perhaps, but I was able to boot Ubuntu 6 from the CD just fine. It seems to be either a problem with the ISO or the CD itself. But I followed the instructions listed here: [https://help.ubuntu.com/community/BurningIsoHowto#In%20Mac%20OS%20X](https://help.ubuntu.com/community/BurningIsoHowto#In%20Mac%20OS%20X) and it didn't work. I also tried burning a second CD at a slower speed (8x infact) and it's simply not booting this way.

Any help/comments/shout-outs would be greatly appreciated. :KS

---

### Post by tiresia on 2008-09-02
Just two stupid questions: Are you sure that you have downloaded the right .iso image for PPC? Have you burned it in OSX on your MacMini, or on another computer? I mean, when you mount it in OSX on the MacMini you can see your CD (is it CD+R?)?
You can try to check the image you downloaded is not corrupted running md5sum (in Mac just md5)

---

### Post by BeautyandSong on 2008-09-02
> **tiresia said:**
> Just two stupid questions: Are you sure that you have downloaded the right .iso image for PPC? Have you burned it in OSX on your MacMini, or on another computer? I mean, when you mount it in OSX on the MacMini you can see your CD (is it CD+R?)?
You can try to check the image you downloaded is not corrupted running md5sum (in Mac just md5)

No such thing as stupid questions my friend! Thanks for responding. 

**Are you sure that you have downloaded the right .iso image for PPC?**

I really don't know, I might have downloaded a version for PC or Intel. This is where it gets a bit tricky, because I want to use this CD to make a LiveUSB key so I can put Xubuntu on my Acer Aspire One laptop. I was wondering if it would work at all. Maybe this is the root of the problem and something that can't be done Mac to Linux. :(

**Have you burned it in OSX on your MacMini, or on another computer?**

I burned it right on my Mini. It's a CD-R, I can see the CD in OS X. It even has it's proper name and everything.

I will look into md5 later on. It's late and I must get sleep. Thank you!

---

### Post by tiresia on 2008-09-02
If I understand what you want to do, you want to install Xubuntu on your Acer Laptop. 
But since your Laptop has no CD-Drive, you want to make an USB-installer, starting your Mac from a Xubuntu Live-CD and using 'Live USB Creator'.

You should first read this link, because if you have Windows on your Laptop, you could create a USB Installer from inside Windows.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you do not have Windows on your Laptop, I suggest you to download the Ubuntu-LiveCD for powerpc from this link (I don't think, that there are Xubuntu-liveCD for Mac):
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
and to burn it at low speed with the Apple Disk Utility.

Before starting the Mac from the LiveCD, download (but most probably you have already it) and move the i86-Xubuntu-Image to / (just outside of your User Account), so that you can access it easily and without sudo or terminal.

Now you can start from the (powerpc) Ubuntu LiveCD (hit C at start up). To mount your USB Memory, got to Places menu and just choose it. Ubuntu will mount it on /media/disk. Do not install Ubuntu on it from the 'Install' icon, because it will install the version for powerpc.

Please note: one important difference between the pc and powerpc version is the bootloader (and the partitions for it). Powerpc Linux uses Yaboot to load the kernel.

---

### Post by BeautyandSong on 2008-09-03
> **tiresia said:**
> If I understand what you want to do, you want to install Xubuntu on your Acer Laptop. 
But since your Laptop has no CD-Drive, you want to make an USB-installer, starting your Mac from a Xubuntu Live-CD and using 'Live USB Creator'.

You should first read this link, because if you have Windows on your Laptop, you could create a USB Installer from inside Windows.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you do not have Windows on your Laptop, I suggest you to download the Ubuntu-LiveCD for powerpc from this link (I don't think, that there are Xubuntu-liveCD for Mac):
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
and to burn it at low speed with the Apple Disk Utility.

Before starting the Mac from the LiveCD, download (but most probably you have already it) and move the i86-Xubuntu-Image to / (just outside of your User Account), so that you can access it easily and without sudo or terminal.

Now you can start from the (powerpc) Ubuntu LiveCD (hit C at start up). To mount your USB Memory, got to Places menu and just choose it. Ubuntu will mount it on /media/disk. Do not install Ubuntu on it from the 'Install' icon, because it will install the version for powerpc.

Please note: one important difference between the pc and powerpc version is the bootloader (and the partitions for it). Powerpc Linux uses Yaboot to load the kernel.

Yes, that is exactly what I want to do. Right now, I ran out of CDs so I haven't tried this yet. But I'm heading to work later today and I will pick up a few. 

If I understand your message correctly: there is no Xubuntu for PPC Macs? My laptop does not have Windows. 

Thank you for the instructions. Like I said, I'm out of CDs for the moment and I am working back-to-back shifts tonight and tomorrow morning. I'll try it out when I get a chance :D

**EDIT: Yeah, Ubuntu loaded. But LiveUSB won't work for PPC. Trying what is listed here: [http://ubuntuforums.org/showthread.php?t=780320](http://ubuntuforums.org/showthread.php?t=780320) But running into more problems. Feels like it's one problem after the next =/ Anyways, consider this thread Resolved. Xubuntu would've never run a live cd since there is none for Mac. Thanks tiresia for the info.**

---

