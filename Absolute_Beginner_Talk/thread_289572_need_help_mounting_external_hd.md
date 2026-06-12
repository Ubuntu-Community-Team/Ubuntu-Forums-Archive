---
title: "need help mounting external hd"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by dfro on 2006-10-31
I got linux running for the first time and now I am working on backup.

To partition an external hard drive, I put the ubuntu install disk in the dvd-rom drive and took the install process up to the point of partitioning the external hd.  Then I quit the install.

When I restarted the computer, the external hd would not mount.  The command 'fdisk -l /dev/sdb' shows that the computer is seeing it, though.
> 
$ fdisk -l /dev/sdb

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+  83  Linux
/dev/sdb2            6375       12748    51199155   83  Linux
/dev/sdb3           12749       19457    53890042+   5  Extended
/dev/sdb5           12749       12876     1028128+  82  Linux swap / Solaris
/dev/sdb6           12877       12888       96358+  83  Linux
/dev/sdb7           12889       19457    52765461   83  Linux


If I try and mount one of the partitions, I get:
> 
$ sudo mount /dev/sdb7 /mnt/sdb7
Password:
mount: you must specify the filesystem type


I tried 'mount -f auto', but no luck.  Any suggestions?  Should I not have partitioned it the way I did?

---

### Post by MyAnda on 2006-10-31
did you format it also? try looking at it with Gparted
(sudo apt-get install gparted) this is a nice little tool
or you can use mkfs.ext3 from the commandline

---

### Post by dfro on 2006-10-31
MyAnda,
  Thank you!  I ran 'mkfs.ext3 /dev/sdbx', where x is all of the partitions that I knew I wanted to be ext3.  I was very happy to see the green led blinking and hear the hd chattering.  I was then able to run 'mount /dev/sdb1  /mnt/sdb1' successfully.  A lost+found directory was put in each /mnt/sdbx directory after I mounted it.  Can I delete those?  Also, is there a config file that remembers where these partitions are mounted?  I want to wipe my internal hard drive clean and do a fresh install of Edgy.
   I have stayed up all night searching in my books and on the web for this answer.  Thanks.  I guess I did not format the drive while in the install mode.  I yanked the install right after the partitioning sequence.
  Do I need to do any formatting of the Extended and the Linux-swap partitions or run any other commands on them?

---

### Post by MyAnda on 2006-10-31
glad to hear you are back in business...good luck!

---

