---
title: "fsck died exit status 8"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by reisewolf on 2008-03-21
High everybody,

 since I want to update to Hardy Heron with a clean system, I would like to get rid of a problem, which always arises when booting. I have to confess that my hard disk is a little bit unorganised since I had earlier Suse 10.3 and I never got rid of these partitions. Anyways when my Ubuntu 7.10 boots it will interupt with the following message:

Log of fsck -C -R -A -a 
Fri Mar 21 12:05:44 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=fa5e0896-cef7-4aff-8865-1e1952ada05b'

/dev/sda6: clean, 30859/1463040 files, 950208/2921814 blocks
fsck died with exit status 8 

Since I am not sure about the Syntax in the different files, I don't dare to change anything without directives, but even I can see that the output of blkid and etc/fstab dont match:

wolfgang@heimwolf:~$ blkid
/dev/sda1: UUID="52E07937E0792281" TYPE="ntfs" 
/dev/sda3: UUID="2666ebde-3bf9-47bd-92f0-9d29e2d66b25" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="68141ec1-53f2-43b5-94f2-6b8f092ddaf9" 
/dev/sda6: UUID="e7ed7761-9732-48e0-bd82-1edff799f185" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="b44cdb24-4976-4cec-bc67-03ccc88c290f" TYPE="ext2" 
/dev/sdb1: UUID="FAF03706F036C921" LABEL="Volume" TYPE="ntfs" 
/dev/sdb2: LABEL="Datenaustau" UUID="091A-091C" TYPE="vfat" 
/dev/sdb3: UUID="A2CC6B72CC6B3FA1" LABEL="Volume" TYPE="ntfs" 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2666ebde-3bf9-47bd-92f0-9d29e2d66b25 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=52E07937E0792281 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=fa5e0896-cef7-4aff-8865-1e1952ada05b /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=e7ed7761-9732-48e0-bd82-1edff799f185 /media/sda7     ext3    defaults        0       2
# /dev/sda5
UUID=68141ec1-53f2-43b5-94f2-6b8f092ddaf9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Could anybody tell me what to do?? Thanks so much for giving attention!!

Regards from Potsdam, Wolfgang

---

### Post by confused57 on 2008-03-22
I don't know if you've found a solution yet or not, but you need to copy & paste the UUID from the output of blkid for /dev/sda6 into your fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

delete the UUID entry in your fstab for /dev/sda6, then copy&paste the UUID from blkid so it looks like this:
```
# /dev/sda6
UUID=e7ed7761-9732-48e0-bd82-1edff799f185  /media/sda6 ext3 defaults 0 2
```
quit & save

When you reboot, youshouldn't get the error message.

---

