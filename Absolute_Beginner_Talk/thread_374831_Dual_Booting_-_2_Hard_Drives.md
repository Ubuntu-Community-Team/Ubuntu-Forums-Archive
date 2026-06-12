---
title: "Dual Booting - 2 Hard Drives?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Araelius on 2007-03-03
I apologize if this topic has been brought up before, but after many attempts to install Ubuntu on my main drive, I have decided to give it a shot on my second drive. The question I had is how is it possible to successfully dual boot using 2 separate hard drives but still being about to choose which to boot into when I start my system? Any help is great appreciated, many thanks in advance.

---

### Post by doc_eman on 2007-03-03
sorry...if you want the best answer, you need to be more specific.
1- bios hard drive order, drive 0 , drive 1...
2- did you install grub? ie;(hd,0) = boot sector. (hd0,0) = /boot/grub.
3- the menu.lst on both drives will be most important, telling grub how to boot second Linux after it's installed...
- my safest tip would be to install your linux on second drive by disconnecting the power of first hard drive, then boot up install it, when finished install, power off plug power to hd1.
when you boot try F8 (your quik bios boot selector) and choose your second drive. it should work, does for me when i try unknown distros. after it boots then i mess with mounting drives and editing grub/menu.lst or etc/lilo.conf and checking for rebooting and menu....
- i'll check back later. 
(BTW - I use a 200mb boot partition just to make it easier. hda1/boot/grub then: for DISTRO kernels:  hda1/boot/ub601_2.6.12/vmlinuz or hda1/boot/xubu610_2.6.18.3/vmlinuz 
also put system.map for each distro in it's folder.
I have splash screens in their folder plus menu.lst backups..)
I'll be more specific when your ready.

---

### Post by ssavelan on 2007-03-03
> **Araelius said:**
> I apologize if this topic has been brought up before, but after many attempts to install Ubuntu on my main drive, I have decided to give it a shot on my second drive. The question I had is how is it possible to successfully dual boot using 2 separate hard drives but still being about to choose which to boot into when I start my system? Any help is great appreciated, many thanks in advance.

Do you run SATA's & SCSI or IDE or a mix?  I find that SATA and SCSI work great together but mixing IDE in is harder as far as I have found.  I quad boot with my main Ubuntu on a 40 gig SCSI and windows/xubuntu/feisty on my 250gig SATA.  It was relatively painless.  Have you tried just having windows booting well off of one hard-drive and then let Ubuntu take the whole of the other?

The defaults should work well.

---

### Post by Edho on 2007-03-03
No problem.

My computer was in origin with 1 harddisk (  C:  ) 30 Gbyte, Win XP on it.
I have mounted the disk from my old broken computer in the current.
And installed Ubuntu (dapper) on that second disk.
During install, Ubuntu will set in the first disk the menu "Grub".
Grub is a bootloader, later you have the choise to boot Win or Linux.

In short :
1,- Put the second harddisk in your computer as slave.
(Maybe you have to move a little bridge...see the notifications on the disk)
2,- Install Ubuntu on the second disk...allow installing Grub on the masterdisk.

---

### Post by ssavelan on 2007-03-03
I agree, giving ubuntu the second disk and putting grub on the master is one of the easiest ways to go. I then make my master a hodge-podge of Windows and experimental distros/configurations of linux.  I always have a good working, solid ubuntu on my slave disk.  The ubuntu installer seems to be pretty keen on properly configuring it all automatically.  I have gotten lucky with the bios's I have worked with, for the most part, though.

What kid of bios are you attempting this dual boot on?

---

