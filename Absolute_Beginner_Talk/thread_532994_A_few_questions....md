---
title: "A few questions..."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by tac603 on 2007-08-23
Hi again.. I've been reading since my last post. I'm both excited and worried at the same time.

I am currently running Windows XP Professional on a SATA HD. And have another 40GB ATA HD for storage purposes. I would like to install ubuntu on the ATA HD. Someone wrote, that I will have to choose which HD/partition should ubuntu install on and have GRUB (no idea what's that) on the primary HD (which is the SATA HD). My concern is, I cannot afford to mess up my primary drive because I have all my project files in there. 

1. Can I install everything including GRUB on the secondary ATA hd ? 
2. Will I be prompted with options to which OS to boot to when I boot the computer?

Thank you and any reply is greatly appreciated.

---

### Post by rexy on 2007-08-23
A boatloader always must be installed on the first sector of a hard drive because that is where the bios starts loading from

So you have two options

1 you tell the bios to boot from disk 2, your new disk, and install the bootloader on that disk
2 you install the bootloader on disk 1 your old disk. Grub will then allow you to boot either ubuntu or windows( or other preinstalled os's)



a boatloader either grub, or the windows bootloader will allow you to boot any os

---

### Post by tac603 on 2007-08-23
Hi.. thanx for the reply. If I may rephrase what u said to double confirm...

Do u mean I can install ubuntu including grud on the ATA harddisk and leave my SATA drive (XP) untouched? If that's what u meant, should I maybe remove the SATA drive prior to installing ubuntu.. or just leave it there so it could detect XP ? erm.. not sure what i ask make sense but hope u get the picture. thank you

---

### Post by rexy on 2007-08-23
ubuntu asks where to install the boot loader so you can tell it to install it on the second disk only. 

That way it will leave the windows disk untouched. It will still add a windows entry to the grub boot loader, im not sure if you can edit that during install, but you can remove it later on if you really want.
All it does is that when you boot grub you get a choice of booting either windows or ubuntu.

You have to remember though that installing grub on the second disks means that everytime your computer boots you have to hit f12 or whatever appropriate key to change the bootdisk.

Just to be really clear The first sector of every disk, and the first sector on every partition can contain a bootloader. This is nothing more then a bit of information which tells the bios where to start loading the os. So there is no real risk with installing grub on your first disk since all it modifies is the first sector on the disc. It then tells your computer that windows can be started by looking on the first sector of the partition windows is on or to start ubuntu from the second disk.

---

### Post by LaRoza on 2007-08-23
You should get the Super Grub Disk. If you need to restore the Windows Boot loader, because you accidently overwrote it, the SGD works wonders. It is always handy to have around.

---

### Post by Steve1961 on 2007-08-23
If you don't want to touch your sata drive at all you could use the windows bootloader to boot linux.  Use the alternative CD to install Ubuntu, and when you get to the part that asks where you want to install grub to, select your root partition (make a not of this during the partitioning stage - /dev/hda1 or something similar).  Then use a live CD (Ubuntu Knoppix whatever) to make a copy of the Ubuntu boot sector, copy this to a usb drive or CD, then boot windows, copy the Ubuntu boot sector to C: and add an Ubuntu entry to boot.ini.  See here for instructions on doing this:

[http://www.oreillynet.com/pub/h/2337](http://www.oreillynet.com/pub/h/2337)

---

### Post by tac603 on 2007-08-23
Thank you all for your replies. I cant help but being extremely paranoid when dealing with linux. I used to dual boot my windows 2000 with redhat some years back.. thought of trying out linux for a change. I successfully dual booted both the OS'es back then with help from some linux forum, unfortunately, i have no idea why redhat, upon boot, everytime runs this fsck thing. Checking on something like a scan disk or some sort and I could hear my hard drive trashing away. Which is why i am not dual booting linux and windows on the same hard drive again. 

I'll try the options mentioned and thanx again all for ur contribution.

---

### Post by asmoore82 on 2007-08-23
install GRUB on the Linux drive and leave the Windows drive completely untouched.
Then, set your BIOS to boot from the Linux drive.
if and when you take out the linux drive in the future,
you will instamagically be back to your original Windows setup: no tears.

(at least "no tears" to boot Windows again, but whenl you actually log in ... :lol:)

---

### Post by tac603 on 2007-08-23
ok what's gonna happen when i actually log in lololol

---

### Post by rexy on 2007-08-23
he's being sarcastic, windows will work fine, you will shed a tear because you booted windows again. at least i think that's what he ment.

---

### Post by tac603 on 2007-08-23
Download completed. Burning now :) :) :)

---

