---
title: "Kubuntu Installation Continually Fails With Totally Broken Grub"
date: 2011-08-25
forum: Apple Hardware Users
---

### Post by MegaLoler on 2011-08-25
I am trying to install Kubuntu on my Mac Mini 2010 Core 2 Duo with 2 gigabytes of ram.  I have tried to do so on both my internal drive and a new external drive, but both end up with a _broken grub_.  *It's not broken as in grub rescue, but it's totally broken and no commands, not even "reboot", will work*.

I can boot from the partition that it was supposedly installed to and I get the broken grub.  In order to boot from the external hard drive I burned an rEFIt disk and booted from the external drive.  It gives the same broken grub.  When I installed grub to the external drive I chose to partition the disks manually and for the grub install location I chose "sdb" which is my external hard drive.  I did not totally overwrite the harddrive with Kubuntu.  I already had an HFS+ partition for Time Machine backups in Mac OS X.  In Mac OS X's disk utility I resized that partition so there was ~100 GB of free space.  In the Kubuntu installer I created a 1 gigabyte swap partition and made the rest of the free space an ext4 partition.

What is weird, though, is that when I booted a live system rescue cd and used the grub command in a terminal I did "root (hd1, 3) and it said that the filesystem was ext2fs.  But the grub will not recognize any other partition's filesystems.

I had no problems installing Ubuntu a while back on this machine.  Can anyone help me?  I really want to get Kubuntu running.  Thanks.

---

