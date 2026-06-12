---
title: "Triple Boot, OS X, Windows 7, and Ubuntu from USB - problems, ideas?"
date: 2012-03-08
forum: Apple Hardware Users
---

### Post by reachcontrol on 2012-03-08
Hey all, 

I'm considering the switch to Ubuntu, after trying a few different liveCDs of Linux desktops.  

I have a MacBook Pro 7,1 core 2 duo, running Snow Leopard 10.6.8, 250Gb HD, 8 Gb RAM, etc. It is currently dual boot (Bootcamp) with OS X and Windows 7.

I'm a student, and have certain programs that (for now) require that I keep my Windows 7 (usually 64-bit, but an issue with the install disc has me using 32-bit, which is corrupted at the moment anyway).  I also want to keep OS X, at least for a while, as that's what I've been using since 2002.

I have scoured numerous sites and forums, and have a few questions and issues.  Ideally, I would like to have a USB-key that I can boot from and USE on my computer, and also move to other Windows-based systems that I have at my many field sites (I'm a wildlife biologist).  

Is this even possible?

Another general question I have is:  If I have a 16Gb USB Thumb Drive, can I have Ubuntu and all my required files on that drive and use the operating system as normal, such that it accesses files on the thumb drive and saves changes to the thumb drive, etc?  So I can move my Ubuntu and files from computer to computer, parasitizing hardware of whatever computer I'm near and running natively.

I have downloaded the current 11.10 .iso file, and attempted to create the USB boot drive using the instructions on the download page.  First off, when I try to "mount" the .iso, I get the message "no mountable file system" but when I try the same with a Fedora .iso, it will actually mount just by double-clicking on the desktop icon (where it's located).

Following the instructions to convert the file to .img and move it to the USB drive works up until i use the dd command.  Once dd is complete, I get a pop-up window with the message "The disk you inserted was not readable by this computer." and options to Initialize, Ignore, or Eject.  

After this point, I try to restart and hold option/alt and only get the Mac and Windows options.

I get the same message with the thumb drive formatted at FAT32 or GUID, always formatted through Disk Utility in OS X.

Sorry for the long post, but I'd really like to sink my teeth into Ubuntu, but can't sacrifice my current operating system(s) until I'm sure I can make the switch.

Thanks for any help.

-Rob

---

### Post by reachcontrol on 2012-03-09
More scouring has turned up these results:

[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88)

[http://ubuntuforums.org/showthread.php?t=1683062](http://ubuntuforums.org/showthread.php?t=1683062)

And it seems that even with rEFIt, having a dual-boot Macbook Pro will prevent you from being able to boot from a USB thumb drive, as you will continually boot back into Windows.

Any other ideas would be appreciated.  And thanks to Neds Moar Salt for the closest I've gotten so far.

-Rob

---

### Post by naggu on 2012-03-09
For your case, I would suggest using Ubuntu in windows/osx using Virtualbox.

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by reachcontrol on 2012-03-11
I'll give that a try.  All this screwing around, and my hard drive has crashed.  I'm running off a liveCD now.  What I may do is dual boot with OS X and Ubuntu, and then run Windows in a virtual machine when my new drive shows up Tuesday.

Doesn't really help me with a portable version of Ubuntu, but I'm going to keep scouring.

---

