---
title: "After a fresh XP/Ubuntu dual boot install, only boots to XP (no grub menu)"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by beatmasterbee on 2006-08-18
Hey,

I have 4 x SATA drives in mt PC.  I have installed a fresh dual boot config of XP and Ubuntu on sda.

sda1 is Windows
sda2 is /home
sda3 is /
sda4 is /swap

After the fresh install of both XP and then Ubuntu on this disk, after a reboot I get no Grub and it just boots straight into XP?  Any ideas?

Please remember I am a total linux noob.

Cheers,
AB

---

### Post by anaconda on 2006-08-18
SO windows wrote over your grub -boot loader.
You have to reinstall grub.

Boot with your Ubuntu liveCD, and go to terminal and type:

grub-install /dev/sda

(if I remember correctly)  Cant check, because I am not home now..

---

### Post by Josh_b on 2006-08-18
There is also another cause.

Check your BIOS to see which hdd has first priority. If your windows drive is first, then you won't see GRUB, but if your Linux drive is first, you will see GRUB.

Hope that helps,
Josh

---

### Post by beatmasterbee on 2006-08-18
No sorry I should have been more clear.

I installed XP first, then Ubuntu.

Xp still boots after reboot.

---

### Post by beatmasterbee on 2006-08-18
It is a dual boot drive...so they are both on the same physical hard drive in BIOS.  It is split into different partitions.

Cheers

---

### Post by anaconda on 2006-08-18
Well, maybe you didn't install grub at all..
But it isn't too late. you can still install it.

---

### Post by yuorz on 2006-08-18
So you only have one hard disk with both Windows and Ubuntu on the same disk just different partitions? If that's the case then you need to re-install grub as anaconda said. 

If they are both on a seperate disks then change the boot priority.

---

### Post by beatmasterbee on 2006-08-18
How?  lol

I just tried to follow your instructions in terminal and got this message:

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.

---

### Post by beatmasterbee on 2006-08-18
How do i reinstall grub in this situation?

Will SGD help?

---

### Post by catlett on 2006-08-18
The problem is sata. Ubuntu's grub is very buggy with sata. What is happening is grub is installed but it isn't on the mbr. You can try a couple of things.
Try installing with the live cd like this [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) The command above does not work on the live cd.
If that doesn't get it on the mbr, you can put grub on a floppy (do you have a floppy? I only ask because not everyone does these days) If you do then the floppy will definately boot first. It isn't perfect but it will get you in(Or least you should)
Just follow the instructions to installed except put fd0 at the end instead of hd0 and have a floppy in as well. 

If those fail, try gag [http://gag.sourceforge.net/](http://gag.sourceforge.net/)
Or the super grub disk [http://adrian15.raulete.net/grub/tiki-list_file_gallery.php?galleryId=1](http://adrian15.raulete.net/grub/tiki-list_file_gallery.php?galleryId=1)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Sorry to post and run but I am off to work. Try to search the forums about sata and grub. There are manyu posts about it but I am afraid to say not many real answers

---

### Post by asfx on 2006-08-18
Hi. Heard that GAG is a good boot manager if you're having trouble with Grub.

Heres a nice page about it:
[http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")

Hope this helps.

---

