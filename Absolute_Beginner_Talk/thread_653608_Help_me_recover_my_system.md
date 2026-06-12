---
title: "Help me recover my system"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by mmikee66 on 2007-12-30
Help!!

My system had 2x80GB hard drives and 2 user profiles running 7.10 

one drive with one partition having the operating system and my /home directory

second dive with two partitions Swap and extra storage.

The second drive with the Swap is dead and the system will not boot into GUI.

How do I reconfigure my system to get a swap on the working drive and not loose any of the /home data?

Can I just reinstall and copy transfer profiles? if that is the case is it better with alternate CD or live CD version of Ubuntu?

---

### Post by Sef on 2007-12-30
First, **back up** all your data.  If you don't, you will likely lose some or all of it.

Second, use the Live CD.  The alternate cd only installs.

Third, how much memory do you have?  If you have more than one gb ram, you really do not need swap unless you are doing some intensive gaming, video editing, or other heavy usage.  

Fourth, to resize the partition, try [GParted]("http://gparted-livecd.tuxfamily.org/").

Fifth, if you have a good extra drive, get [clonezilla]("http://gparted-livecd.tuxfamily.org/").  Note: there is a clonezilla-GParted Live CD on the site.

---

### Post by RudolfMDLT on 2007-12-30
boot into recovery mode, give the root password and edit the fstab file:
> 
 sudo nano /etc/fstab

look for the line containing:
> /dev/sdb6 none **swap** sw 0 0


and comment it out
> **#**/dev/sdb6 none **swap** sw 0 0

Like Sef said, swap isn't critical and you can work without it, for now.

Now  press CTRL+X and save changes.

restart the machine:
> sudo shutdown -r now

Now Ubuntu should boot. Either way, post back and lets see what the problem is.

Goodluck,

Rudolf

EDIT: The profiles you are talking about are on the drive that is OK, so you won't loose them yet! :) Like Sef said, backup! Try the above and lets get you back into a point and click environment and then we can do backups before we repartition.

---

### Post by mmikee66 on 2007-12-30
thanks Sef and RudolfMDLT,

I will try that when I get home.

/home Data is intact as I can see it when running DSL.

Will feed back in about 8 hours

---

### Post by mmikee66 on 2007-12-30
typing this from my desktop. fixed it in about 1 minute with the instructions.
This is the fstab after repairing the problem.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0d105d6-a941-4daf-9146-158d7a95999e /               reiserfs notail      $
# /dev/sdb1
#UUID=1673c97e-9b69-4346-aafe-065f80f74a3a /extstorage       reiserfs notail     $
# /dev/sda5
UUID=ea50f34e-4449-41bd-b18f-60967c8280c9 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Realized the dead drive was sdb1. All I needed to do was # out the line with the drive UUID.

---

