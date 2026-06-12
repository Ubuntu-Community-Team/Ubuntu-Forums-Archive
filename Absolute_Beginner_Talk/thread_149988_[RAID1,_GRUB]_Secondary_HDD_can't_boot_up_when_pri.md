---
title: "[RAID1, GRUB] Secondary HDD can't boot up when primary HDD fails"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-25
RAID 1
-------

/dev/md0 consists of /dev/sda1 and /dev/sdb1
/dev/md1 consists of /dev/sda2 and /dev/sdb2

/dev/md0 is used as /boot
/dev/md1 is used as physical volume of LVM

LVM
----

/dev/md1 is the physical volume of a volume group with logical volume for swap and root.

Grub has been installed on the second harddisk's MBR with

grub> root (hd1,0)
grub> setup (hd1)
grub> quit

However, after I remove the first harddisk (/dev/sda), the system can't boot up with the second harddisk. Just a blank bootup screen.

Any advice please?

Thanks !

---

### Post by jason.b.c on 2006-03-25
[QUOTE=Akhran]RAID 1
-------

/dev/md0 consists of /dev/sda1 and /dev/sdb1
/dev/md1 consists of /dev/sda2 and /dev/sdb2

/dev/md0 is used as /boot
/dev/md1 is used as physical volume of LVM

LVM
----

/dev/md1 is the physical volume of a volume group with logical volume for swap and root.

Grub has been installed on the second harddisk's MBR with

grub> root (hd1,0)
grub> setup (hd1)
grub> quit

However, after I remove the first harddisk (/dev/sda), the system can't boot up with the second harddisk. Just a blank bootup screen.

Any advice please?

Thanks ![/QUOTE]

After you remove the hard drive from the computer???
Are you taking the drive out of the computer??

---

### Post by Akhran on 2006-03-25
To simulate failure of the primary HDD, the primary HDD (/dev/sda) is removed from the computer, and the computer is started with only the secondary HDD to test if the secondary HDD will boot.

[QUOTE=jason.b.c]After you remove the hard drive from the computer???
Are you taking the drive out of the computer??[/QUOTE]

---

