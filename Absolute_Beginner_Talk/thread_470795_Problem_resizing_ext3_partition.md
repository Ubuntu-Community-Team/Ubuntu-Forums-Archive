---
title: "Problem resizing ext3 partition"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by iZmu on 2007-06-11
I was trying to expand my ext3 partition and I followed this [howto]("http://www.howtoforge.com/linux_resizing_ext3_partitions_p2"). Everything was going well until I had to reboot in order to resize the filesystem. When typing
$ e2fsck -f /dev/sda2
the output is not the expected:
----------------
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...

e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
----------------
i'm freaking out here..
any suggestions?they'll be much appreciated...
Thanks

---

### Post by iZmu on 2007-06-11
is this an uncommon problem? Is there anyhing i can do to resolve it?

Thanks

---

### Post by iZmu on 2007-06-11
ok, i'm kind of desperate here...
I'm using knoppix to expand the ext3 partition..
i ran fsck on sda2 (the partition i want to expand), and removed the journal to change its type to ext2..
Then, i used fdisk to delete the partition and to create a new one, specifying the first and last cylinder, so it would enclose the free space i had behind the partition and the partition itself.I finally wrote the partition table on disk (using w) and quit fdisk. So far, so good... Here's when the problems started. I rebooted and went back on Knoppix.then I tried to run e2fsck /dev/sda2 and the output was the error posted above.
anyway, here it is:
> e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...

e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
So now i can't resize the filesystem, can't undo what i've changed in the partition table, and obviously can't boot with ubuntu nor windows because grub won't work (gives error 17).

Is there any hope for me?
Please help :(
Thanks

---

