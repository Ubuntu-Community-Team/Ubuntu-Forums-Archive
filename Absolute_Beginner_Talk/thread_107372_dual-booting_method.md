---
title: "dual-booting method"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by anoncompboy on 2005-12-22
I have decided not to install GRUB. [This article]("http://ezinearticles.com/?Dual-Boot-Windows-and-Linux:-Single-and-Multiple-Hard-Drives&id=99860") teaches me how to dual-boot the 'real way' without GRUB. I want to do it this way, but I do not understand what this means:

> From the shell in your Linux installation (boot from your installation disks): Execute the following shell command, replacing /dev/hda3 with the location of your Linux boot partition.

shell# dd if=/dev/hda3 of=/bootsect.lnx bs=512 count=1

Doing this is supposed to create a copy of the linux boot sector, bootsect.lnx

So when/where do I type the command "shell# dd...." ? Type it after the "boot:" text in the install CD of ubuntu, or do something in the ubuntu OS?

---

### Post by darth_vector on 2005-12-22
that article contains many an untrue statement. i dont know why you wouldnt want GRUB on the MBR (and no, the windows bootloader doesnt **have** to occupy the MBR, it just has to 'think' that it does. GRUB fools it very nicely thank you very much), but if you do i would find another howto guide from someone that:

1) doesnt lie to you
2) gives you better instructions

good luck :)

---

### Post by anoncompboy on 2005-12-22
thanks lol ya that article did seem kind of fishy - the guy contradicts himself, he says not to use the GRUB then he says its his favorite :confused: 

I decided to use the grub. I may change and use the windows dual boot later, atleast after I get comfy with ubuntu a bit.

---

### Post by towsonu2003 on 2005-12-22
I would just ignore that article. It seems it did not do enough research... 
From the article: > Windows and Linux: Same Hard Drive The windows operating system MUST occupy the master boot record (MBR). Linux, on the other hand does not have to. In this scenario, you must install windows first! After Windows has been successfully installed, then you can install Linux. This is critical! The Linux "boot loader" is called GRUB. When you install Linux—MAKE SURE YOU DO NOT INSTALL THE LINUX BOOT LOADER TO THE MBR.
Tell that to my MBR :) I have windows + ubuntu and grub is installed to mbr. Windows never complained. 

Also, you might want to reconsider because once you do what it says, this forum won't be able to help you with your boot issues effectively. Here is an example how that might happen: 
Q: I lost windows, cant boot into it
A: reinstall grub (link to howto)
Q: Don't use grub, I use this (link to your article)
A: Sorry, dont know that. 

But if you really want, good luck ;) Learning is good, regardless of what you learn.

---

### Post by jimrz on 2005-12-23
yuo might want to take a look [**[COLOR="Sienna"]here[/COLOR]**]("http://users.bigpond.net.au/hermanzone/")
I followed this "how to" article a few weeks ago on my 1st ever linux install (ubuntu /XP dual boot) and it worked perfectly and has been ever since.

Welcome and good luck.

---

