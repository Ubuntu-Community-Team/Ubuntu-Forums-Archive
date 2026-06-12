---
title: "Questions about GRUB and Partitioning"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by Goober on 2005-09-30
I am not quite sure where this post belongs, but, since I am a newbie to partitioning and GRUB, here is probably good enough.

1 - I want to install some more Linux Distros on my Computer, probably DSL, Kubuntu, Fedora.  Currently, I have Ubuntu and XP dual-booting.  If I install more Linux Distros, can I access them through GRUB?  Can GRUB have a list of like 3-4 OS's to choose from?

2 - I also want to partition my HDs to put more Distros on, probably on my 160 Gig that I have Ubuntu on.  Should I partition it before I start the installation process for the new Distro with Ubuntu, or should I do it during the install process?

3 - Will GParted (which looks like a Ubuntu partitioning program) work for the 160 Gig?  It recognizes both of my HDs, the 40 Gig I don't want to touch, but it shows my 160 Gig with Ubuntu as having an partly filled "ext3" format, which i assume is Ubuntu, and the rest just being "fat32" that is, well, just sitting there.  I guess I would partition the fat32?

Thanks in advance for the answers!

---

### Post by bored2k on 2005-09-30
1. Yes, GRUB can support many more Operating Systems than that.
2. Some distributions have sloppy partitioners. If you think you have a good partitioner forehand, go ahead. Some could even crap up your NTFS drivers.
3. I'm not sure GParted is completely stable, but it should work.

---

### Post by Goober on 2005-09-30
4 - Hrm . . . Ok, then is there a different Partitioner for Ubuntu other then GParted?

5 - What format should I partition in, ext3 or fat32?

6 - Also, it says "boot" and "Iba" under the "Flags" column for the 160 Gig HD that Ubuntu is installed on, with the Ubuntu part saying "boot".  That part is kinda obvious, but what about the "IBA" partition, or do I need to worry about this?

---

### Post by aysiu on 2005-09-30
[QUOTE=Goober]
1 - I want to install some more Linux Distros on my Computer, probably DSL, Kubuntu, Fedora.  Currently, I have Ubuntu and XP dual-booting.  If I install more Linux Distros, can I access them through GRUB?  Can GRUB have a list of like 3-4 OS's to choose from?[/quote] At a certain point I was quadruple-booting, but triple-booting is a good thing. You can have XP and Ubuntu, then another partition just for playing around with (the distro of the moment). What I do is keep Ubuntu's Grub on the MBR and just copy the /boot/grub/menu.lst entry from the new distro to Ubuntu's /boot/grub/menu.lst.

> 
2 - I also want to partition my HDs to put more Distros on, probably on my 160 Gig that I have Ubuntu on.  Should I partition it before I start the installation process for the new Distro with Ubuntu, or should I do it during the install process? Yes. I'd advise resizing and creating a new partition with DiskDrake (even if you're not going to install Mandriva). Otherwise, QTParted is good.

> 
3 - Will GParted (which looks like a Ubuntu partitioning program) work for the 160 Gig?  It recognizes both of my HDs, the 40 Gig I don't want to touch, but it shows my 160 Gig with Ubuntu as having an partly filled "ext3" format, which i assume is Ubuntu, and the rest just being "fat32" that is, well, just sitting there. GParted should be fine. Keep in mind, though, that partitioning programs cannot resize partitions that are mounted, and if the GParted program lives on the hard drive that's being resized, that hard drive is probably mounted.

---

### Post by bored2k on 2005-09-30
5. For a linux install? Definitely NOT FAT32. I suggest you go with ReiserFS. ReiserFS is faster than EXT3 while EXT3 is slightly more stable. I use ReiserFS and it rocks. A lot of us do.

6. Once you have partitioned, you can let the Ubuntu installer do the rest. Just point it to the right direction and let him fly.


It is not hard at all so don't be scared.

---

### Post by quattroman on 2005-09-30
I dont wanna start a thread for the following question, and I see people talk about it here
What is GRUB?

thanks

---

### Post by bored2k on 2005-09-30
[QUOTE=quattroman]I dont wanna start a thread for the following question, and I see people talk about it here
What is GRUB?

thanks[/QUOTE]
> GRUB is a GPLed bootloader intended to unify bootloading across x86
 operating systems.  In addition to loading the Linux kernel,
 it implements the Multiboot standard, which allows for flexible loading
 of multiple boot images (needed for modular kernels such as the GNU Hurd).
The bootloader.

---

### Post by Goober on 2005-10-01
Ok, I have successfully formatted my partition into reiserfs from ext3.

Thanks a lot for the help, you guys.  And I have a fairly good idea of what I am doing, I just am a fairly cautious person, and like to have all my questions answered before I do anything.

---

### Post by bored2k on 2005-10-01
Better safe than sorry.

---

