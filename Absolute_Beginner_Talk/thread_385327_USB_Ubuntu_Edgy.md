---
title: "USB Ubuntu Edgy"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by gingin on 2007-03-15
**Actualy Im not able to perform formating Usbdisk and set the partition size and instal Ubuntu.**


There is original tutorials>


   1. Insert a 1GB or larger USB flash drive
   2. Open a terminal window and type sudo su
   3. Now type fdisk -l to list available drives/partitions (note which device is your flash drive example: /dev/sdb)
          * type umount /dev/sdb1 (replacing sdb1 with your flash drive partition)
          * type fdisk /dev/sdb (replace sdb with your device)
          * type p to show the existing partition and d to delete it
          * type p again to show any remaining partitions (if partitions exist, repeat step 3)
          * type n to make a new partition
          * type p for primary partition
                o type 1 to make this the first partition
                o hit enter to use the default 1st cylinder
                o type +700M to set the partition size
                o type a to make this partition active
                o type 1 to select partition 1
                o type t to change the partition filesystem
                o type 6 to select the fat16 file system
          * type n to make another new partition
                o type p for primary partition
                o type 2 to make this the second partition
                o hit enter to use the default cylinder
                o hit enter again to use the default last cylinder
                o type w to write the new partition table
   4. Type umount /dev/sdb1 (replacing with your partition) to ensure the partition is unmounted
   5. Type mkfs.vfat -F 16 -n USB /dev/sdb1 (replace sdb1 with your partition) to format the first partition
          * &#8220;Alternately you can try mkfs.vfat -F 32 -n USB /dev/sdb1 (doesn&#8217;t work on every system)&#8221;
   6. Type mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2 to format the second partition (replace sdb2 if necessary)
   7. Remove and Re-insert your flash drive
   8. Download the USBEdgy.zip and select the option to open with Archive Manager
   9. Once the download has finished, use the Archive Manager to &#8220;extract&#8221; the contents of the zip your USB partition.
  10. Back at the terminal, type sudo apt-get install syslinux
  11. Type sudo apt-get install mtools
  12. Type syslinux -sf /dev/sdb1 (replace sdb1 if necessary)
  13. Reboot your computer and set your system BIOS to boot from USB-HDD or USB-ZIP. Also set the boot priority if necessary.

**That I did was this **
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 1046 MB, 1046782464 bytes
63 heads, 32 sectors/track, 1014 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1015     1022232+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 62, 32) logical=(1014, 8, 17)
root@ubuntu:/home/ubuntu# fdisk /dev/sda

Command (m for help): p

Disk /dev/sda: 1046 MB, 1046782464 bytes
63 heads, 32 sectors/track, 1014 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1015     1022232+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 62, 32) logical=(1014, 8, 17)

Command (m for help): d
Selected partition 1

Command (m for help): p

Disk /dev/sda: 1046 MB, 1046782464 bytes
63 heads, 32 sectors/track, 1014 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): d
No partition is defined yet!

Command (m for help): /dev/sda d
/: unknown command
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): 


****

---

### Post by steve.horsley on 2007-03-15
It looks to me like you deleted the only partition. You got this far in the tutorial:
> 1. Insert a 1GB or larger USB flash drive
2. Open a terminal window and type sudo su
3. Now type fdisk -l to list available drives/partitions (note which device is your flash drive example: /dev/sdb)
* type umount /dev/sdb1 (replacing sdb1 with your flash drive partition)
* type fdisk /dev/sdb (replace sdb with your device)
* type p to show the existing partition and d to delete it
* type p again to show any remaining partitions (if partitions exist, repeat step 3)

And according to the tutorial, the next step is **n** to create a new partition:
> * type n to make a new partition
* type p for primary partition
o type 1 to make this the first partition
o hit enter to use the default 1st cylinder
o type +700M to set the partition size
o type a to make this partition active
o type 1 to select partition 1
o type t to change the partition filesystem
o type 6 to select the fat16 file system
* type n to make another new partition
o type p for primary partition
o type 2 to make this the second partition
o hit enter to use the default cylinder
o hit enter again to use the default last cylinder
o type w to write the new partition table


---

