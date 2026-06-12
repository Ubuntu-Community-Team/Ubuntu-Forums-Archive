---
title: "fsck failed while booting"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by dijxtra on 2007-03-29
While booting, I get some kind of "fsck failed" error. So I turned boot logging on. Now, when I choose Ubuntu from grub menu, it displays the grey screen with Ubuntu logo and the log saying that everything is booting fine... except that "Starting Bootleg deamon" has a nice red FAILED designation. Then it goes on booting and then crashes, and I have to type "exit" to make Ubuntu boot properly. After I type "exit" and press return, the system finishes loading and everything is fine.

Here's what the /var/logs/boot has to say:

nick@rilmir:/var/log$ sudo cat boot
Thu Mar 29 20:25:01 2007: ^[[74G[^[[31mfail^[[39;49m]
Thu Mar 29 20:25:01 2007: ^[[74G[ ok ]ng disc parameters...       ^[[80G
Thu Mar 29 20:25:01 2007:  * Checking root file system...       ^[[80G /: clean, 73612/3842720 files, 491062/7681078 blocks
Thu Mar 29 20:25:01 2007: ^[[74G[ ok ]
Thu Mar 29 20:25:01 2007: ^[[74G[ ok ]ing modules...       ^[[80G
Thu Mar 29 20:25:02 2007: ^[[74G[ ok ]up ifupdown...       ^[[80G
Thu Mar 29 20:25:02 2007: ^[[74G[ ok ]ng module dependencies...       ^[[80G
Thu Mar 29 20:25:05 2007: ^[[74G[ ok ]odules...       ^[[80G
Thu Mar 29 20:25:05 2007: ^[[74G[ ok ]he system clock...       ^[[80G
Thu Mar 29 18:25:04 2007: ^[[74G[ ok ]p LVM Volume Groups...       ^[[80G
Thu Mar 29 18:25:04 2007: ^[[74G[ ok ]Enterprise Volume Management System...       ^[[80G
Thu Mar 29 18:25:05 2007:  * Checking all file systems...       ^[[80G Failed to open the device '/dev/hdc2': No such file or directory
Thu Mar 29 18:25:05 2007:
Thu Mar 29 18:25:05 2007:
Thu Mar 29 18:25:05 2007: Reiserfs super block in block 16 on 0x302 of format 3.6 with standard journal
Thu Mar 29 18:25:05 2007: Blocks (total/free): 7681072/6848376 by 4096 bytes
Thu Mar 29 18:25:05 2007: Filesystem is clean
Thu Mar 29 18:25:05 2007: Replaying journal..
Thu Mar 29 18:25:05 2007: Reiserfs journal '/dev/hda2' in blocks [18..8211]: 0 transactions replayed
Thu Mar 29 18:25:08 2007: Checking internal tree..finished
Thu Mar 29 18:25:08 2007: ^[[74G[^[[31mfail^[[39;49m]
Thu Mar 29 18:25:08 2007:
Thu Mar 29 18:25:08 2007:  ^[[31m*^[[39;49m fsck failed.  Please repair manually.
Thu Mar 29 18:25:08 2007:
Thu Mar 29 18:25:08 2007:  * CONTROL-D will exit from this shell and continue system startup.
Thu Mar 29 18:25:08 2007:
Thu Mar 29 18:25:08 2007: root@(none):~# \007~exit
Thu Mar 29 18:25:33 2007: bash: ~exit: command not found
Thu Mar 29 18:25:33 2007: root@(none):~#
Thu Mar 29 18:25:35 2007: root@(none):~# exit
Thu Mar 29 18:25:36 2007: exit
Thu Mar 29 18:25:36 2007:  * Mounting local filesystems...       ^[[80G mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
Thu Mar 29 18:25:39 2007:        missing codepage or other error
Thu Mar 29 18:25:39 2007:        (aren't you trying to mount an extended partition,
Thu Mar 29 18:25:39 2007:        instead of some logical partition inside?)
Thu Mar 29 18:25:39 2007:        In some cases useful info is found in syslog - try
Thu Mar 29 18:25:39 2007:        dmesg | tail  or so
Thu Mar 29 18:25:39 2007:
Thu Mar 29 18:25:39 2007: mount: special device /dev/hdc2 does not exist
Thu Mar 29 18:25:39 2007: mount: special device /dev/hdc6 does not exist
Thu Mar 29 18:25:39 2007: /dev/hda1 on /media/hda1 type ntfs (rw)
Thu Mar 29 18:25:39 2007: /dev/hda2 on /media/hda2 type reiserfs (rw)
Thu Mar 29 18:25:39 2007: /dev/hda6 on /media/hda6 type vfat (rw)
...

And, this is what Partition Magic says about my disk drives:

Disk 1 (194474)
*NTFS (80.003,4)
*Linux Ext2 (30.004,2)
*Linux Ext2 (30.004,2)
*Extended (54.462,5)
**Linux Swap (1.004,0)
**FAT32 (53.458,5)

Disk 2 (78159)
*Unalocated (7,8 )
*Extended (78.152,1)
**FAT32 (78.152,1)

One of those two Ext2 partitions is in fact ReiserFS, but Partition Magic obviously can't tell between Ext2 and ReiserFS.

Anyway, what happens here? Why is that fsck failed error appearing?

---

### Post by NyteGeek on 2007-03-30
boot from the live cd and run fsck on the affected file systems and see what happens.

---

