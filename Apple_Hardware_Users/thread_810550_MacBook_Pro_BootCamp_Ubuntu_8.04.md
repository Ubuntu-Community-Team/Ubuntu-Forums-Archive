---
title: "MacBook Pro BootCamp Ubuntu 8.04"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by oceanfirehawk on 2008-05-28
Hello everyone. I finally got Ubuntu to work via the bootcamp partition. i am running refit to boot ubuntu. when i select linux from the boot menu....eventually a screen comes up with the following message and instructs me to pick the one I want to boot with:

ubuntu 8.04, kernel 2.6.24-17-generic
ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
ubuntu 8.04, kernel 2.6.24-16 generic
ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
ubuntu 8.04, memtest86t

other systems:
generic (on/dev/sda3)
generic (recoverymode) (on/dev/sda3)
memtest 86t (on/dev/sda3)



I usually select the very first one. the partition was originally supposed to be at 16GB, but it shows 8.something on the desktop. how do i get the space back and fix this. i used the instructions at [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) to install ubuntu.
Thanks in advance for any help
Jake

---

### Post by cyberdork33 on 2008-05-28
> **oceanfirehawk said:**
> The partition was originally supposed to be at 16GB, but it shows 8.something on the desktop. how do i get the space back and fix this. i used the instructions at [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) to install ubuntu.
Thanks in advance for any help
Jake
Please give output of:
```
sudo parted /dev/sda print
```
and
```
sudo fdisk -l /dev/sda
```

---

### Post by oceanfirehawk on 2008-05-28
> **cyberdork33 said:**
> Please give output of:
```
sudo parted /dev/sda print
```
and
```
sudo fdisk -l /dev/sda
```

1) Disk /dev/sda: 200GB

Sector size (logical/physical): 512B/512B

Partition Table: gpt



Number  Start   End    Size    File system  Name                  Flags

 1      20.5kB  210MB  210MB   fat32        EFI System Partition  boot 

 2      210MB   183GB  182GB   hfs+         Untitled                   

 3      183GB   191GB  8219MB  ext3                                    

 5      191GB   198GB  7218MB  ext3                                    

 6      198GB   199GB  1000MB  linux-swap                              

 4      199GB   200GB  1000MB  linux-swap                              



Information: Don't forget to update /etc/fstab, if necessary.     


2) Usage: fdisk [-b SSZ] [-u] DISK     Change partition table

       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)

       fdisk -s PARTITION           Give partition size(s) in blocks

       fdisk -v                     Give fdisk version

Here DISK is something like /dev/hdb or /dev/sda

and PARTITION is something like /dev/hda7

-u: give Start and End in sector (instead of cylinder) units

-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by cyberdork33 on 2008-05-28
I think you may have used 'i' instead of 'l' for the second command, but it's OK. you seem to have two linux partitions and two swap partitions.

Boot from the Ubuntu Live CD, and start gparted. (System > Administration > Partition Editor)

You need to delete one of the ext3 partitions, and one of the swap partitions ( I think partition #5 and #6) then resize partition #3 to take up the freed space. I am pretty sure that partition 5 and 6 are not being used because the MBR partition table on your Mac is limited to 4 partition, and GRUB uses that to boot Ubuntu. 

Either way, if doing the above breaks your install, you just have to install again using the partitions already created.

---

### Post by oceanfirehawk on 2008-05-28
Hi and thanks for trying to help :)

i deleted one of the linux os's on the partition and couldnt delete the swap space because it was shown as being locked and the delete button was grayed out and not selectable. i booted again and synced the partitions with refit. booted again and now its a command prompt that says grub> 



question? on the page that i used to install ubuntu (the wiki page)...why does it want you to install ubuntu twice?

---

### Post by cyberdork33 on 2008-05-28
> **oceanfirehawk said:**
> Hi and thanks for trying to help :)

i deleted one of the linux os's on the partition and couldnt delete the swap space because it was shown as being locked and the delete button was grayed out and not selectable. i booted again and synced the partitions with refit. booted again and now its a command prompt that says grub> 



question? on the page that i used to install ubuntu (the wiki page)...why does it want you to install ubuntu twice?because there is a mistake. I tried to edit it yesterday to fix it.

---

