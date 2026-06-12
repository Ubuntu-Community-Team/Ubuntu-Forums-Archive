---
title: "mounting drives and moving home"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-05-04
I have 2 250 gig drives in this box partitioned in approximately halves. Initially, I was dual booting into XP and had one partition formatted ext3, with the others NTFS (set up so Ubuntu can r/w). I have gotten most of what I need working fine, and decided to dump Windows. I unmounted two of the NTFS partitions and reformatted them as ext3. I commented out the entries for these two partitions that were NTFS in the fstab file, removed the Windows entry in the GRUB menu, and rebooted. Everything seems to be OK as far as functioning.  I am going to leave one of the partitions as NTFS for now. Here is how I would like to set everything up:

1) Mount the second half of the first drive (the one with Ubuntu on it) and move my $home there.
2) mount the second half of the second drive and use it as a backup partition.


I looked at the fstab file and can't make heads or tails of the entry for the mounting of the ext3 drive.

I guess I have two questions:

First, how do I mount the two partitions (persistent), and second, how do I move my $home directory to one of them? What about copying the files that are in the $home? I would hate to change something and lose all of the configuration and installations that I have done.

If it helps, here are my fstab and fdisk -l :

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2         639     5124735   83  Linux
/dev/hda2           15125       30401   122712502+   f  W95 Ext'd (LBA)
/dev/hda3   *         640       15124   116350762+  83  Linux
/dev/hda5           15360       30401   120824833+  83  Linux
/dev/hda6           15125       15359     1887574+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       16708   134206978+   7  HPFS/NTFS
/dev/hdb2   *       16709       30515   110904727+  83  Linux


Here is fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=0ece6fbf-e6c7-4487-99a3-d78409d928f1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=2fda5d1c-1502-4faf-ad53-9fa6d1e5f98b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
#/dev/hda5	/media/Windows	ntfs-3g	defaults,locale=en_US.utf8	0	0
#/dev/hdb2	/media/Windows2	ntfs-3g	defaults,locale=en_US.utf8	0	0
/dev/hdb1       /media/windows3 ntfs-3g defaults,locale=en_US.UTF-8 0 0


Thanks for all of the help.

Forgot to say that I am using Edgy and don't plan to upgrade until I get more familiar with Ubuntu.

Thanks for all of the help. I did the temp mount and copied the home folder to it, then set it up in fstab and rebooted. Works great. (I did do a backup of the home directory to the other drive before I did it)

---

### Post by antoz on 2007-05-04
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

Can't really help myself but the links may hep, A

---

### Post by ubnewbie2 on 2007-05-04
Moving home is fairly easy.  Mount the new partition to a temporary mount point, say /mnt/temp, and copy all the home directories/files to it. Make sure permissions/ownerships don't change. Then remount  it to /home.

Probably safer/easier to do this as root, so you aren't actually using any of the home files.

Alter/add the fstab entry to automatically mount this to /home at boot time.

You could clean up the real /home directory before you mount the new partition over the top of it (which will hide the files in it) to get the space back on your root drive.  The really paranoid amongst us might even put a copy of the home files somewhere else until this all works, just in case something goes wrong :-)

---

