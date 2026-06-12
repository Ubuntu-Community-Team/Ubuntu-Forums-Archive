---
title: "Macbook Woes..."
date: 2009-03-21
forum: Apple Hardware Users
---

### Post by SweetDaddyJones on 2009-03-21
Hello all!  I'm sad to say i created a big mess trying to dualboot ubuntu and mac os x on a Macbook 1,1, and could really use some help on what to do next.  Right now, rEFIt appears on startup and OSX is working fine, but the Ubuntu partition shows up as "Legacy OS" and gives a message like "No operating system.  Reboot your computer" 

Here's how i created this problem:

 I'm very new to linux in general (been triple booting xp/vista/ubuntu for about a month), and although i wouldn't yet say i'm really comfortable, i understood the process on my PC well enough that i thought the macboook would pose no problem.  (I have only ever owned windows PCs and know very little about Macs) Apparently i overestimated myself.


At first, BootCamp would not partition the disk, so i used Carbon Copy Cloner to made an external backup, installed refit, and booted up from the external. I then was able to successfully partition the disk into one 30GB HFS+ partition for OSX and one 44.5 GB partition (deleted and left as free space for Ubuntu).  Nothing new yet.

Then, i think this may have been a mistake:  It took more than an hour to clone the 23 GB of data from the macbook to the external so i could safely erase and partition the HD, and I didn't want to wait another hour to clone it back before installing Ubuntu.  I didn't see any reason why i couldn't install ubuntu first and then copy the OSX data afterward.  Ubuntu install went fine, the 44.5 GB of free space went to a 3gb swap space at the end of the drive and the rest ext3.  

At this point, both Ubuntu (from the HD) and OSX (from the external) were showing up and booting/working properly from rEFIt.  In my mind, everything was properly set up and the only thing i had to do was wait for the hour it would take CCC to clone OSX back to the internal HD.

Somewhere along the line, I think made a careless mistake with bootloaders - probably in where/how GRUB was installed - because after the cloning finished, the problems started.  Sometimes refit wouldn't show up at all on startup, other people were tinkering so i can't be sure of everything that was done, but i know that i foolishly left a CD with GAG bootloader on it in the drive (which was probably a mistake to involve GAG at all in the first place).  But now the ubuntu partition reads "legacy OS" and won't start.  I'm guessing that since i made the clone of OSX before installing Ubuntu that when i restored it, i lost the grub-efi that told ubuntu how to boot?  In any event, i ended up deleting the Ubuntu partition.

I want to reinstall Ubuntu, but I need help first!  Can anyone tell exactly where i went wrong?  If I just reinstalled without (Initially that is, i know i made many more mistakes in trying to correct the first..)  Also, since ext3 is not natively supported in OSX, would it be better to use most of the space as a FAT32 partition?  Or to make the HFS+ partition much larger and just use that for storage?  I just want the ability to choose which operating system i start and be able to read/write my files from either! 

Thank you in advance!  I really REALLY appreciate the help and am trying to understand! 


Nicolas

---

### Post by Joushou on 2009-03-21
"Operating system not found" simply means it couldn't find any boot instructions, or in your case, grub. To fix it now, reinstall grub (It's in the sticky faq, and since I'm on my g1, and it's 1:00am, you'll gonna have to find it yourself ;) ).
To avoid the problem, click "Advanced" at the installation summary, and make sure you install grub to your root partition (or your boot partition, which I doubt you have).
If it happens again, it's not a big deal, it's easy to fix (Still in the FAQ).

For you second question, I wouldn't use fat32 for anything, but I'm not sure about the hfs support... haven't tried write, only used the default read-only...
If hfs+/x support is stable enough, that would be what I would choose.

Hope that helps :)

---

### Post by cyberdork33 on 2009-03-21
Refer to the installation doc:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

You just need to make sure the partition tables are in sync and that you have grub installed to the Ubuntu root partition.

You mention grub-efi, but you didn't say anything about installing it. grub-efi is completely different from grub. You really only use one of these methods, not both.

---

### Post by SweetDaddyJones on 2009-03-22
First of all, i want to thank both of you for your help - both OSes are now booting properly and all seems to be in order!  I think i understand about grub/grub-efi/refit now too - refit just SELECTs which drive to boot from, but grub has the actual instructions for how to boot linux (which is why it must be installed on the same partition)?  Boot loader vs boot selector?  Sorry about the questions, i want to understand how it works, not just make the problems go away heheh.   Thanks guys!  You really did me a service!

---

### Post by cyberdork33 on 2009-03-22
> **SweetDaddyJones said:**
> First of all, i want to thank both of you for your help - both OSes are now booting properly and all seems to be in order!  I think i understand about grub/grub-efi/refit now too - refit just SELECTs which drive to boot from, but grub has the actual instructions for how to boot linux (which is why it must be installed on the same partition)?  Boot loader vs boot selector?  Sorry about the questions, i want to understand how it works, not just make the problems go away heheh.   Thanks guys!  You really did me a service!
refit is a pretty menu interface to the EFI firmware on your Mac (and a few nifty utilities like the EFI console, the partition tool, and Paritition Inspector.app). It can launch efi executables directly, but that is about it.

grub is a bootloader. it can actually load the linux kernel into memory and start the machine using that code. It is also capable of passing control of the boot process to another loader. It is a legacy loader though, and requires certain BIOS calls and MBR information to be useful (these things are emulated on your mac).

grub-efi is an efi executable version of the new grub2 (not yet final). Using refit to launch grub-efi, and using that to load linux would be the ideal way to do things as it does not rely on any emulation of legacy components. However, there is still a lot of work that needs to be done to get GRUB working well enough to fully replace GRUB(1).

---

