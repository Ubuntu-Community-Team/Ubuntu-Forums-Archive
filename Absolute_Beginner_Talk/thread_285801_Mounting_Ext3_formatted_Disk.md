---
title: "Mounting Ext3 formatted Disk"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2006-10-27
Currently evaluating Ubuntu - previous experience Windows only. 

I started on a spare computer with a virgin 24 Gb disk. Ubuntu installed perfectly and have been getting to grips with the Linux world. 

Today, I wanted to expand my storage so I could transfer my music collection to the Ubuntu system. I added a 160Gb drive to the system. Using the live CD - Gparted, I partioned the drive in 2 partitions. First making an extende of the full capacity followed by a two logical partition of 70Gb and 78Gb. This reported no errors. 

I rebooted the pc, this time with the on-disk operating system of Ubuntu. In computer I can now see:

CD-Rom/DVD-rom Drive
70.9 Gb Volume
78.1 Gb Volume
Filesystem

Unfortunately, I can't mount the two created partitions. Did I do something wrong or are there more steps to get this working. 

Intention is to have these both volumes accesible (mounted) upon bootup.

---

### Post by kidders on 2006-10-27
Hi there,

I wonder if the new partitions got formatted. If you've only just created them, then you might as well do it again anyhow! There are various "mkfs" tools for you to try, for a range of filesystems, just in case you want to try something other than Ext3.

The next thing to try is mounting them manually, to see what happens. Something like **mount /dev/sdb1 /mnt/test**, assuming /mnt/test exists, of course. If that works for you, you can make the arrangement permanent by adding a line to your /etc/fstab for each new filesystem.

Hope that helps.

**Edit:** One additional issue that seems to confuse some people is that, just like Ubuntu's root filesystem, there's no reason why Linux would let anyone but root write files in your new partitions. Among the many ways of granting a "normal" user write access to the disk is to create him a directory of his own with **mkdir /mnt/test/Music && chown user:user /mnt/test/Music** for instance.

---

### Post by Belgatom on 2006-10-27
Works now, although I gave permissions via Nautilus. Now, how do I go about it making this a permanent mount.

***edit***
Woops sorry, didn't see the Fstab reference.

---

### Post by BLTicklemonster on 2006-11-01
Interesting stuff, I'm trying to get dapper to show up on my edgy

---

