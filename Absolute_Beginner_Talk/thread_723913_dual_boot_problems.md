---
title: "dual boot problems"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by catroaring on 2008-03-14
So i decided to try out fedora.  i used gparted live-cd to repartion my drive that gutsy is on.  so i would have 2 big partitions.  when i installed fedora 8 and rebooted it gives me no option to run ubuntu.  the ubuntu partion is still their.  

heres my fdisk -l

[root@localhost ~]# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x220a5000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      208813+  83  Linux
/dev/sda2           18988       19457     3775275    5  Extended
/dev/sda3   *        9950       18987    72597735   83  Linux
/dev/sda4              27        9949    79706497+  8e  Linux LVM
/dev/sda5           19223       19457     1887606   82  Linux swap / Solaris
/dev/sda6           18988       19222     1887574+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2cb3844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14945   120045681    7  HPFS/NTFS

Disk /dev/dm-0: 80.2 GB, 80228646912 bytes
255 heads, 63 sectors/track, 9753 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 1342 MB, 1342177280 bytes
255 heads, 63 sectors/track, 163 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30307800


tx for any help

---

### Post by SpenceMakesSense on 2008-03-14
One solution is to install grub and it should give you the choice of both. also if your willing if you just install Ubuntu again it would give you the choice of choosing fedora.

---

### Post by catroaring on 2008-03-14
> **SpenceMakesSense said:**
> One solution is to install grub and it should give you the choice of both. also if your willing if you just install Ubuntu again it would give you the choice of choosing fedora.
grub is installed but ubuntu doesnt show.  the filesystem is on the drive i can browse through it, while in fedora

---

### Post by SpenceMakesSense on 2008-03-14
you could try reinstalling grub via Ubuntu cd [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This helped me after windows deleted grub.

---

### Post by alphaniner on 2008-03-14
Maybe when fedora installed grub it didn't detect your ubuntu install for some reason.  Open your /boot/grub/menu.lst file (fedora partition) and see if there are any entries for Ubuntu.  If not, mount the ubuntu partition from fedora (if you can) or while running the ubuntu live cd and make a note of the menu.lst on the ubuntu partition.  Then add those entries to the fedora menu.lst (after making a backup of course).

---

### Post by sandysandy on 2008-03-14
> **catroaring said:**
> grub is installed but ubuntu doesnt show.  the filesystem is on the drive i can browse through it, while in fedora


no issue at all.

(a) edit menu.lst file of ubuntu and make entry for fedora in it. ( use ubuntu live CD)

(b) with super grub disk load grub of ubuntu.

(c)  on rebooting - u will get grub of ubuntu with optiion for both fedora and ubuntu

revert back if more info is required.

regards

---

### Post by catroaring on 2008-03-14
> **SpenceMakesSense said:**
> you could try reinstalling grub via Ubuntu cd [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This helped me after windows deleted grub.
[B] 	
SpenceMakesSense[/B]

thanks, worked like a charm!  :)

---

