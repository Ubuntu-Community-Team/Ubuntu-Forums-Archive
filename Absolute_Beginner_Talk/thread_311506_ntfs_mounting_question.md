---
title: "ntfs mounting question"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by pizzutz on 2006-12-03
I have been running Ubuntu for about a week now.  Great job guys.

I have 2 HDs. An 80 Gb IDE which is now running Dapper, and a 160 Gb SATA which is partitioned into 2 NTFS drives, the first of which has my winblows instalation and programs, and the second of which is movie and music files.

I am not concerened about data corruption. there is nothing I need on the other drive just some stuff I'd like to have if possible so I am using ntfs-3g package to mount them.  I have no problems with mounting the data partition, but when I try to mount the OS partition, I get this error
[INDENT]
pizzutz@mike-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/satamain
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' mount option.
[/INDENT]

My problem is my windows installation is way screwed up (although the partition is physicaly fine)  It constantly crashes and always schedules a disk check even when I shut down.  (Which is the main reason I decided to try Ubuntu)  but I cannot find any force option for the mount command.  now since 

mount -t ntfs /dev/sda1 /media/satamain

mounts fine, just without the permissions I want, I must assume this option is added with ntfs-3g.  I know mount -t ntfs-3g works cause I can umount and mount my data partition with it.

I realize this is more of a ntfs-3g question than an ubuntu question, but any suggestions on how to force that partition to mount would be appreciated.

for reference
[INDENT]pizzutz@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/satamain ntfs-3g defaults.locale=en_US.utf8  0  0
/dev/sda2       /media/satadata ntfs-3g defaults.locale=en_US.utf8  0  0
[/INDENT]

---

### Post by sardion on 2006-12-03
I am not certain about this since I ditched my ntfs partition (and all of M$) a while back but I think to force it you need to put force in your fstab like this:

/dev/sda1 /media/satamain ntfs-3g force,defaults.locale=en_US.utf8 0 0
/dev/sda2 /media/satadata ntfs-3g force,defaults.locale=en_US.utf8 0 0


But, I caution you, I am not sure what force does but it could screw up your data I suspect since it would be enabled by default if it was 100% safe.

You may also want to try running chkdsk some other way, I think if you boot off a windows xp cd you can try to "repair" your disk or some such.  But I really have no clue about that side of things.

Hope this helps.
Good luck.

---

### Post by bodhi.zazen on 2006-12-03
To force a check use the option force:
```
mount -t ntfs /dev/sda1 /media/satamain -o force
```

There is mention of booting into windows, but I do not know if this is absolutely necessary.

Why don't you pull your data off these partitions and re-format to a Linux Native file system (ext3) ?

---

### Post by pizzutz on 2006-12-03
yup, that did it. thank you.

I do intend to reformat soon, but there are a few more things I need to learn to do in Ubuntu before I can completly get rid of M$.

---

