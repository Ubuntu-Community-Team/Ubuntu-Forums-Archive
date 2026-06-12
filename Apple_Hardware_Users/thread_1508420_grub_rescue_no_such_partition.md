---
title: "grub rescue no such partition"
date: 2010-06-12
forum: Apple Hardware Users
---

### Post by razercultmember on 2010-06-12
So i think i screwed up my entire hard drive by using Disk Utility to delete supposedly only the ubuntu partitions

I also had rEFit but i deleted the efi folder manually

error: no such partition
grub rescue>

thats what i get when i try to boot my mac book pro 5,5 up

also to note is that i used ubuntu off the cd and i saw that the one partition on my hard drive was completely empty?!?

I am using the latest 10.04 Ubuntu LTS version

help?!

I ran ubuntu through the cd and i found that the one partition on it was empty  but around 20 gigs remain but i cant find them

---

### Post by pytheas22 on 2010-06-13
What is the output of:
```

sudo fdisk -l
cat /boot/grub/grub.cfg
```

---

### Post by razercultmember on 2010-06-13
should i put that in terminal in the livecd boot or the

grub rescue>

?

---

### Post by razercultmember on 2010-06-13
put in terminal in live cd


ubuntu@ubuntu:~$ cat /boot/grub/grub.cfg
cat: /boot/grub/grub.cfg: No such file or directory
________________________

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

---

### Post by pytheas22 on 2010-06-13
Sorry, it should be in the terminal in the live CD.  Also, the command you ran was mistyped--you had a '1' instead of an 'l' (lowercase L).  Please run again:
```

sudo fdisk -l
```

You should get output containing information about the different partitions on your hard disk.

The other command won't work because you're running in a live environment (my fault for failing to think about that).  You can still get the information you need, however, by going to the Places menu while running the live CD and selecting your Ubuntu hard disk (if you're not sure which entry under Places corresponds to Ubuntu, just try them until you find the right one).

After selecting the disk, and window should open containing a bunch of folders.  One of the folders should be labeled "boot".  Open that folder and look for a folder inside named "grub".  Open "grub" and look for a file named "grub.cfg".  Open that file and paste the contents here.

---

### Post by razercultmember on 2010-06-13
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002b6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312571223+  af  HFS / HFS+

and there is no grub.cfg file only the grubenv file :|

---

### Post by pytheas22 on 2010-06-13
Thanks for the output.  Is there a menu.lst file instead of a grub.cfg?  If you have original grub installed instead of grub2, that would be the case.  grub2 has been the default in new Ubuntu installations now for about a year now, but if you installed it earlier than that you would likely have old grub.

The point of seeing the menu.lst or grub.cfg file is to know which parameters grub is trying to use to boot your operating system.  Without that information, it's hard to know what could be going wrong, so unfortunately I can't really make any suggestions yet.  If you can find menu.lst, please post it.  If it's easier, you could also just press 'e' at the grub menu, which should show you the full list of boot parameters that it's using.

Another option, if you no longer plan on having Ubuntu on this system at all, is to boot to your OS X installation CD and try to have that fix the boot configuration.  It will probably erase grub, but allow you to boot OS X again.  I've never done that myself, but it seems like it might be the easiest solution, since it appears that you only have one operating system installed anyway.

---

### Post by tactician1016 on 2010-06-21
I an having the exact same issue now. I tried to boot the snow leopard install disc, but it just went back to the "grub rescue"  screen again, and no commands worked. any ideas? Are there any commands i can put into the grub rescue? By the way, macbook pro 6.2 (the i5)

---

### Post by wilee-nilee on 2010-06-21
> **tactician1016 said:**
> I an having the exact same issue now. I tried to boot the snow leopard install disc, but it just went back to the "grub rescue"  screen again, and no commands worked. any ideas? Are there any commands i can put into the grub rescue? By the way, macbook pro 6.2 (the i5)

Your going to want to start your own thread for the best chance of getting help.;)

---

### Post by JohnAtilano on 2010-06-21
> **razercultmember said:**
> So i think i screwed up my entire hard drive by using Disk Utility to delete supposedly only the ubuntu partitions

I also had rEFit but i deleted the efi folder manually

error: no such partition
grub rescue>

thats what i get when i try to boot my mac book pro 5,5 up

also to note is that i used ubuntu off the cd and i saw that the one partition on my hard drive was completely empty?!?

I am using the latest 10.04 Ubuntu LTS version

help?!

I ran ubuntu through the cd and i found that the one partition on it was empty  but around 20 gigs remain but i cant find them

I'm assuming you DO NOT have a backup.  If you do, I would boot from your backup, reformat and repartition using disk utility and then clone from your backup.

Have you tried booting while holding down the OPTION key?  Often, this will enable me to boot into OS X.  Once you do, ensure you go into System Preferences --> Startup Disk and choose your hard drive as the start up disk.  rEFIt was your startup disk but you deleted it.  I'm guessing you did not choose a new start up disk.

---

### Post by tactician1016 on 2010-06-21
> **JohnAtilano said:**
> I'm assuming you DO NOT have a backup.  If you do, I would boot from your backup, reformat and repartition using disk utility and then clone from your backup.

Have you tried booting while holding down the OPTION key?  Often, this will enable me to boot into OS X.  Once you do, ensure you go into System Preferences --> Startup Disk and choose your hard drive as the start up disk.  rEFIt was your startup disk but you deleted it.  I'm guessing you did not choose a new start up disk.

Thank you. I had the exact same issue. Holding down Option works perfectly (note: if you have the mac os install disk and a backup like i did, you're golden. If not, OPTION still works very well. Thank you for saving my computer.

---

