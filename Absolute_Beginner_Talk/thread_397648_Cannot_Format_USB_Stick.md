---
title: "Cannot Format USB Stick"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-03-30
I am trying to install Ubuntu Edgy on a USB Stick.

At one point the tutorial from [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) asks me to run
```
sudo mkfs.vfat -F 16 -n liveusb /dev/sdb1
```
The output is
```
steve@steve-laptop:~$ sudo mkfs.vfat -F 16 -n liveusb /dev/sdb1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: /dev/sdb1 contains a mounted file system.

```
Does this mean it failed? I should mention that the second try to format the second partition was successful. The command and output is below
```
steve@steve-laptop:~$ sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=casper-rw
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
64320 inodes, 64260 blocks
3213 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=67108864
2 block groups
32768 blocks per group, 32768 fragments per group
32160 inodes per group
Superblock backups stored on blocks: 
        32768

Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

---

### Post by eljalill on 2007-03-31
The output from the first partitions says, that the file system on it is mounted, which basically means, that your computer is using it or is keeping it ready for use.
Do ```
 sudo umount /dev/sdb1 
``` and you should be able to format.

---

