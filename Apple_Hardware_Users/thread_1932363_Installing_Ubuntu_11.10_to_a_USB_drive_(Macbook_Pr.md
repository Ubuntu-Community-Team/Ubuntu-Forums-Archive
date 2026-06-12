---
title: "Installing Ubuntu 11.10 to a USB drive (Macbook Pro 8,1)"
date: 2012-02-27
forum: Apple Hardware Users
---

### Post by drewbharris on 2012-02-27
I'm trying to make a bootable USB drive on my Macbook and having no luck.

Basically, I can run a live environment from one USB drive using an EFI tool I found here, involved dropping the .ISO and some EFI files onto a USB drive.  Unfortunately, when I run this USB drive and install to the destination USB drive, the destination won't boot.  I made sure I installed the bootloader to the correct drive, and I have rEFIt.  rEFIt detects the drive as a Linux install but when it will not boot, just hangs for about 10 seconds and then boots my internal Windows bootcamp install.


Any ideas?

edit:  I don't want to have a purely live environment, I'd like to have a full install on the destination drive (it's 8 GB).

---

### Post by musicman10489 on 2012-02-28
I think I am slightly confused. Are you booting up from **one** usb drive and then trying to install onto **another**? 

*edit:* Either way [this]("http://azcrumpty.weebly.com/1/post/2011/10/full-usb-flash-drive-install-with-ubuntu-1110-oneiric-ocelot.html") may be of some interest to you. It seems the method here is to boot the iso under a VM and then do a full install to the desired USB drive. So you may want to try this from Windows/OS X or whatever else you have on the Macbook.

---

### Post by drewbharris on 2012-02-29
> **musicman10489 said:**
> I think I am slightly confused. Are you booting up from **one** usb drive and then trying to install onto **another**? 

*edit:* Either way [this]("http://azcrumpty.weebly.com/1/post/2011/10/full-usb-flash-drive-install-with-ubuntu-1110-oneiric-ocelot.html") may be of some interest to you. It seems the method here is to boot the iso under a VM and then do a full install to the desired USB drive. So you may want to try this from Windows/OS X or whatever else you have on the Macbook.

Ahaha, yes, that's precisely what I'm trying to do.

I'll check out this scenario.  I actually did get a live OS running from the install USB, but installing to the destination USB did not yield a bootable environment.

IIRC the [installer] problem is that Ubuntu does not have hardware support for the most recent MBP DVD drives.

edit: Upon reading this guide, it looks good for installing to the destination drive but doesn't help the fact that I can't boot the installed USB system on my Mac, not even from rEFIt :/

---

### Post by musicman10489 on 2012-02-29
Alright, I see what you're saying. I'll keep looking around but if anybody else here with more knowledge than I wants to step in and save the day, please do so :P

---

### Post by gordintoronto on 2012-02-29
> **musicman10489 said:**
> I think I am slightly confused. Are you booting up from **one** usb drive and then trying to install onto **another**?

I did exactly that on my HP laptop, didn't have to do anything unusual. No EFI to confuse things.

---

### Post by azcrumpty on 2012-03-16
[Booting can be debugged]("http://scaryreasoner.wordpress.com/2009/08/29/debugging-the-linux-boot-process/"). You can turn off the spash screen to see what is going on and [edit the grub options ]("http://www.gnu.org/software/grub/manual/html_node/Configuration.html")so they pause long enough to enter commands.  

You mentioned it appears to hang but if you can find out what went wrong, we should be apply a fix.



 > **drewbharris said:**
> Ahaha, yes, that's precisely what I'm trying to do.

I'll check out this scenario.  I actually did get a live OS running from the install USB, but installing to the destination USB did not yield a bootable environment.

IIRC the [installer] problem is that Ubuntu does not have hardware support for the most recent MBP DVD drives.

edit: Upon reading this guide, it looks good for installing to the destination drive but doesn't help the fact that I can't boot the installed USB system on my Mac, not even from rEFIt :/

---

### Post by azcrumpty on 2012-03-18
I've seen this before.  The installer sets the boot to wait for ten seconds since there are choices.  It also sets the boot up to the computer's physical drive.  If it didn't and you removed the removable drive, your computer wouldn't start.  The blank screen was due to a need to replace &#8220;quiet splash&#8221; with &#8220;nomodeset&#8221; in the grub boot.

---

