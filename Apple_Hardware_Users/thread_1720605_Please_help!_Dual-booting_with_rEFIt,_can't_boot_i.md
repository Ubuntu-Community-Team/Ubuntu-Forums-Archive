---
title: "Please help! Dual-booting with rEFIt, can't boot into ANYTHING!"
date: 2011-04-03
forum: Apple Hardware Users
---

### Post by Dysruption on 2011-04-03
I am in dire need of help. I decided I wanted to dual-boot my 24" iMac with Ubuntu 10.10 and it's current OSX Leopard. 

I installed rEFIt on my OSX install, and then created a partition for the Ubuntu install and swap space.

rEFIt, my OSX, and my Ubuntu ran perfectly fine until I was on my Ubuntu and attempted to install and play the game Heroes of Newerth. Once I started up the game for the first time, my system froze. 

So, I held the power button down to shut it down. Then, I turned my computer back on. My computer goes to the rEFIt menu, but if I try to boot into either OSX or Ubuntu, my computer just hangs at the loading screen. (the gear spins in OSX, freezes, and then the computer restarts) (In Ubuntu, it usually just stays on the maroon screen, then restarts)

I have tried booting into Single-User mode, I have tried booting from the install disk, and I have tried booting from holding Option at start up and directly booting into linux. 

The ONLY time I can do ANYTHING is when I hold Option, boot into Linux from there, then it brings me to the GRUB menu, from which I choose 32-bit recovery mode, and then go into the Fail-safe low graphics mode. That is where I am typing to you right now. 

If anyone has ANY help it would be greatly appreciated, for I basically don't have a computer right now!

Thanks!

---

### Post by fela on 2011-04-03
I was going to say you crapped out your hard disk, but then I noticed that you can't boot the install disk...

I don't know how you set the boot device priority on macs, however what I would do is set it to CDROM, and try to boot something like the system rescue CD, or just any linux live cd (or is that what you already tried doing?). If you manage to get that to boot, you can at least try to mount your drives to make sure you still have all your data (as that isn't certain at the moment).

Or else you could try plugging a different hard drive into the PC and see if it boots anything.

---

### Post by Dysruption on 2011-04-03
> **fela said:**
> I was going to say you crapped out your hard disk, but then I noticed that you can't boot the install disk...

I don't know how you set the boot device priority on macs, however what I would do is set it to CDROM, and try to boot something like the system rescue CD, or just any linux live cd (or is that what you already tried doing?). If you manage to get that to boot, you can at least try to mount your drives to make sure you still have all your data (as that isn't certain at the moment).

Or else you could try plugging a different hard drive into the PC and see if it boots anything.

There is no boot priority change as far as I know, but you can hold C at startup to boot from a disk, which is what I have tried.

As far as the live CD goes, I can't eject the recovery disk now because I can't even get into the linux recovery mode that I was in before. Now I am on my old 2003 Dell, which sucks. 

However, when I was in the recovery mode, I ran Disk Utility to check if the harddrive was okay, and it said it was.


Btw, thanks for your help fela.

Please, anybody else, I still need help.. I have no idea what to do. My computer won't boot into ANYTHING at all now.

---

### Post by Dysruption on 2011-04-03
Sorry for the DP, but if anyone could just tell me a way to disable and/or remove rEFIt without booting into anything, that would be great. Thanks!

---

### Post by fela on 2011-04-03
About ejecting the recovery disk, there should be something on the CD drive to force it to eject, normally it's a small hole that you put a paperclip down.

After you've ejected the CD, I would try booting OS X in verbose mode, using command+V while starting up, to see if any obvious error messages come up.

Also, you could try reinstalling Ubuntu to the same partition, to at least get an OS running on it.

---

### Post by Dysruption on 2011-04-03
> **fela said:**
> About ejecting the recovery disk, there should be something on the CD drive to force it to eject, normally it's a small hole that you put a paperclip down.

After you've ejected the CD, I would try booting OS X in verbose mode, using command+V while starting up, to see if any obvious error messages come up.

Also, you could try reinstalling Ubuntu to the same partition, to at least get an OS running on it.

I have ejected the disk, and put in a Ubuntu Live CD. It won't boot from that or run the installer from that.

I have, however, figured out how to go into Single-User mode, bringing me to a command prompt. I restored my EFI partition, which I had accidentally deleted. Still no luck. I also can't boot into safe mode.

When running verbose mode, it gets to a certain point and then stops completely.

---

### Post by fela on 2011-04-03
> **Dysruption said:**
> I have ejected the disk, and put in a Ubuntu Live CD. It won't boot from that or run the installer from that.

I have, however, figured out how to go into Single-User mode, bringing me to a command prompt. I restored my EFI partition, which I had accidentally deleted. Still no luck. I also can't boot into safe mode.

When running verbose mode, it gets to a certain point and then stops completely.

How did you restore the EFI partition? Also, what point does it stop when booting?

Also, does it not give an error when trying to boot the CD?

---

### Post by Dysruption on 2011-04-04
> **fela said:**
> How did you restore the EFI partition? Also, what point does it stop when booting?

Also, does it not give an error when trying to boot the CD?

Well I followed these instructions: [http://www.ehmac.ca/anything-mac/43204-restore-efi-partition-proper-bootcamp-operation.html](http://www.ehmac.ca/anything-mac/43204-restore-efi-partition-proper-bootcamp-operation.html) 

After messing around with it, here's what happens now.

I deleted rEFIt, but that didn't solve anything. So now, when I turn it on, the computer boots straight to the Apple Screen. The gear underneath the Apple spins for awhile, then it freezes. Usually it then restarts, and repeats the process. 

The same thing happens when I boot from a CD or try to boot in safe mode.  

When I hold Option to see where I am booting from, it shows my HD as "EFI Boot" which it never did before. 

I was able to boot DBAN (Darik's Boot and Nuke) to attempt to wipe my HD, but when I tried to wipe my HD it never worked. Now I can't even get DBAN to boot up. 

Things I can do:
Boot into Single User Mode
Boot into Hardware Test Mode

---

### Post by fela on 2011-04-04
First of all, why would you want to wipe your HDD? Is there no data on this PC?

Second, unless someone has a better idea, what I would do is restore OS X using an install disk (there should be an option to restore the OS while keeping data I would have thought).

There is probably a way of getting out of the mess it's in right now, but I think it would be too time consuming for me to try to work it out (as opposed to reinstalling the OS). Obviously, **if someone has a better idea, please say.**

---

### Post by sauferkel on 2011-04-04
i'm not sure at the moment if u are able to boot from the osx dvd.
if u can, try his way, or maybe this can help u? 
i just found this in the triple-boot guide, it should help against a wrongly installed grub into the mbr(?)


Find your Mac OS DVD (and insert into drive)
Reboot holding down Alt/Option
Once setup has loaded choose your language
Click Utilities->Terminal...
Type "fdisk -u /dev/rdisk0" <ENTER>
Type "y" <ENTER>
Quit Terminal, Quit Installer

---

### Post by fela on 2011-04-04
> **sauferkel said:**
> i'm not sure at the moment if u are able to boot from the osx dvd.
if u can, try his way, or maybe this can help u? 
i just found this in the triple-boot guide, it should help against a wrongly installed grub into the mbr(?)


Find your Mac OS DVD (and insert into drive)
Reboot holding down Alt/Option
Once setup has loaded choose your language
Click Utilities->Terminal...
Type "**fdisk** -u /dev/rdisk0" <ENTER>
Type "y" <ENTER>
Quit Terminal, Quit Installer

I'd say it's better to do this using the disk utility. Just open disk utility from the menu. For example, fdisk doesn't support GPT.

---

### Post by sauferkel on 2011-04-04
yeah, sorry ;)
the disk utility is indeed the better solution

---

### Post by Dysruption on 2011-04-04
I can ONLY boot the install disk in single-user mode it seems. If I try and boot the CD normally it just freezes up again.

And the reason I tried to wipe it is because I have most of the data backed up, and I thought maybe wiping the entire thing and THEN installing would solve the problems.

---

### Post by fela on 2011-04-04
> **Dysruption said:**
> I can ONLY boot the install disk in single-user mode it seems. If I try and boot the CD normally it just freezes up again.

And the reason I tried to wipe it is because I have most of the data backed up, and I thought maybe wiping the entire thing and THEN installing would solve the problems.

OK, what you could do is boot the CD in single user mode, wipe the HDD from there (using diskutil from the command line), and then try to install.

---

