---
title: "Ubuntu 12.10 wont progress past the boot menu on any of my Macs (Mac Mini, Macbook)"
date: 2012-11-01
forum: Apple Hardware Users
---

### Post by linkandzelda on 2012-11-01
Hello there everyone.
I've recently made the decision to switch over full time to Ubuntu as my native Operating System on my Mac Mini 2011 and Macbook Air 2010. I did some research before to make sure it was possible, and it seems there is a large community for Ubuntu on Mac Intel.

I followed a guide to make a bootable USB installer for Ubuntu 12.10. I tested it on my Windows PC and it booted fine. Then I tested it on the macs and it didn't work. On the Mac Mini it booted into a black screen forever after selecting the disc in the startup manager from pressing alt key, and on the Macbook Air it booted into my bootcamp instead, completely skipping the Ubuntu boots menu, and yes I did select the Ubuntu stick it just skips right past it. I also have rEFIt installed on the Macbook Air.

I gave up with this as I was unable to find a solution, and got out a USD DVD drive and burned a DVD, then attempted to boot it from my Macbook Air. I was able to do this and got to the Ubuntu boot menu, but after selecting Try Ubuntu, I get a blank screen flashing "_". This is the same when I go to install it too.

I've come to these forums to request assistance, as I'm rather annoyed with Apple products at this very minute, that it takes so much hassle to get this to run.

Thanks in advance,
Kris

---

### Post by mfox on 2012-11-01
I am able to boot up a Ubuntu 12.10 live usb disk on my 13" MBA 2010, which I made on a PC running Ubuntu using unetbootin. Everything works fine except persistence (I have a thread started on this problem), but this suggests that the problem isn't hardware.  What is different between your setup and mine is that you are running BootCamp and rEFit and I am not, but I don't see why that should stop your MBA from booting up a live disk.  I am running Mountain Lion on my MBA, but even if you are running something earlier, I don't see how that would affect a startup from a Ubuntu disk, since that comes into play before the MacOS is started.  I did do the recent firmware update; perhaps that affects things.  However the more likely possibility is either the process used to create the disk, the possibility that you had some errors in the download or the OS you used to make the disk.  If you can, I suggest the following:
- download the live iso again and check it for integrity
- use unetbootin on a computer running Linux or PC if possible, not your Mac

By the way, I can make changes to the Live usb on a PC that stick, but as soon as I boot the usb on my MBA, I can't see the changes and I can't make any further changes.  So while a live usb can be booted from a Mac or PC, something is different about the way it operates on these two platforms.

I hope that helps.

---

### Post by linkandzelda on 2012-11-01
Thanks for the reply. I used the LiLi Linux creator from a Windows virtual machine to make the USB installer, which totally failed to boot on both macs. Then I tried the Live CD and that boots the boot menu on the MBA, but boots nothing on the Mac Mini. I just totally don't believe it.

I'll redownload the image and burn to another disc and try again. On the MBA I'm running Mountain Lion, same as my Mac Mini. Totally makes no sense why it doesn't work, and I have no errors to go off of either.

---

### Post by linkandzelda on 2012-11-01
So I came across a post and found this bootloader CD. [http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)

Using that I burnt it to a disc and booted it from my MBA. Then selected to boot from USB. After about a minute I'm greeted with an Ubuntu desktop, which has a few graphical glitches unfortunately, but that's definitely a step forward! Have yet to try the same method on Mac Mini, or even an installation.

EDIT: Installed and booted Ubuntu on the MBA with no hicks!

---

### Post by mfox on 2012-11-02
> **linkandzelda said:**
> So I came across a post and found this bootloader CD. [http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)
...
EDIT: Installed and booted Ubuntu on the MBA with no hicks!

Glad to hear it! Were you able to create a persistent usb (one that saves changes you make)?

---

