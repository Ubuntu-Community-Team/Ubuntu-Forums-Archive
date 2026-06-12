---
title: "Update to 2.6.14 ate my drive"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by vatechtigger on 2007-04-05
Sorry if there is no easy way to explain this with my limited experience

So I have a dual boot on a PATA drive with windows XP. I also have 2 serial ata drives, one formated to NTFS (called WindowsStore) for windows storage with a fat 32 for transfer (Win-Ubuntu), and the other SATA formated ext3 called (LinuxStore) . I had everything set up and mounting in 2.6.13 and then tonight I get prompted to download updates. When I reboot under 2.6.14 my /dev/hda drive no longer shows up (looked in gparted) even though that is where I am booting from of course. It now shows sda, sdb and sdc. with one of the actual 200gb serial drives not available. 

if i restart and choose 2.6.13 in grub, everything boots up swell shows all my hd and sd drives and partitions. So what happened?

---

### Post by crispy_420 on 2007-04-05
What format is the "missing" drive?

---

### Post by chalex on 2007-04-05
AFAIK there's some new lowlevel libata changes that make all drives now appear through the scsi layer or something like that.  So you'll see your /dev/hda now appear as /dev/sda.

It sounds to me like your drives under 2.6.13 are called /dev/hda, /dev/sda, /dev/sdb and under 2.6.14 they are /dev/sda, /dev/sdb, /dev/sdc.  when you're using the new kernel, try "sudo fdisk -l" to show the partitions on all the drives, although I guess you'll see the same info using gparted.

---

### Post by crispy_420 on 2007-04-06
So does an edit of fstab solve the issue?

---

### Post by vatechtigger on 2007-04-06
thanks for the replies guys. 

yes, all the drives now appear as sda, sdb and sdc, instead of hda, sda and sdb I guess since the fstab wasn't updated to reflect the changes to the kernal the mounting of my partitions is all messed up. 

Can I delete the fstab all together say after unplugging my 2 extra drives. (ie will ubuntu create a new one based on just my boot drive) that I can then repopulate with my 2 storage drives?

So Im thinking since my fstab still has references to hda in it that everything sort of got shifted to the right, and bumped my drive (200 GB SATA ext3) off the list. :O

---

### Post by crispy_420 on 2007-04-06
I think it may be a bad idea to delete completely, just need to edit it.

---

### Post by vatechtigger on 2007-04-07
Can I just change the hda to the appropriate sda designations? The main drives boot drives are designated with UUID's. Do these need to change along with the drive designation?

---

### Post by DigitMole on 2007-04-09
Got mine eaten also. Started with hdd1(40 gig), hdc1(40 gig), and sda5(80 gig).  After Feisty fawn I am now sda1(40 gig), sdb1 (40 gig), and sdc5(80 gig). 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=1c38bcc4-3f0a-4bde-a6a8-b565e95733b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd1
UUID=3eef42bc-3055-4558-8dc7-16e8b37166c6 /home           ext3    defaults        0       2
# /dev/sda5
UUID=42BB-2749  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=13183bd7-b5df-49a7-ae08-ac201c1fdea7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda5	/media/sda5	vfat	iocharset=utf8,umask=000   0       0

RESULTS FROM FDISK -l

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2340    18796018+  83  Linux
/dev/sda2            2341        2482     1140615    f  W95 Ext'd (LBA)
/dev/sda5            2341        2482     1140583+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4866    39086113+  83  Linux

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        9964    80027797+   f  W95 Ext'd (LBA)
/dev/sdc5               2        9964    80027766    b  W95 FAT32

Gparted List the drives as: sda, sdb, sdc

tried to run "ls /dev/disk/by-uuid/ -alh" but still could only see the two 40 gigs.
any Ideas??????

---

### Post by vatechtigger on 2007-04-09
[http://ubuntuforums.org/showthread.php?t=403975](http://ubuntuforums.org/showthread.php?t=403975)

here is how I fixed it.

---

