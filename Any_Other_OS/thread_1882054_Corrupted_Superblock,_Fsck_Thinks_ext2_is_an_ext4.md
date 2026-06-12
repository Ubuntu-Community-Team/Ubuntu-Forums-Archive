---
title: "Corrupted Superblock, Fsck Thinks ext2 is an ext4"
date: 2011-11-16
forum: Any Other OS
---

### Post by Fajner1 on 2011-11-16
Running Linux Mint 12 RC here.

Ok, I booted from a LiveUSB (also LM12RC) and decided to expand my /home partition. While it was still reading it, seeing how long it took, I canceled it. Even though it didn't actually do anything yet, the superblock was corrupted. I followed the tutorial at [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/) to repair it , but it seems to think that my ext4 partition is an ext2 partition, and isn't working.


```

mint@mint ~ $ sudo fsck.ext4 -v /dev/sda8
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda8

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

mint@mint ~ $ sudo mke2fs -n /dev/sda8
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
23904256 inodes, 95599104 blocks
4779955 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
2918 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968

mint@mint ~ $ sudo e2fsck -b 819200 /dev/sda8
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sda8

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

mint@mint ~ $ sudo e2fsck -b 8193 /dev/sda8
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sda8

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```I tried all the blocks (not shown), and also the ext2 block it suggested, but it didn't work.

---

### Post by Perfect Storm on 2011-11-16
Moved to Other OS/Distro Talk.

---

### Post by Fajner1 on 2011-11-16
It has nothing to do with distros...

---

