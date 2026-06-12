---
title: "Very confused about partitions!"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-02-24
I have two hard drives in my system.

1. An IDE 120GB in two partitions (XP on half and a 'temp' drive in ext3 format on the other)
2. A SATA 375GB in three partitions (Ubuntu, Swap and 'Data' also in ext3 format)

My fstab is as follows:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a975b903-02a5-4a42-ae2c-f6dbe9e7d8f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=e95bd3d7-76a5-4dac-8f83-4cef1a80401a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb5	/home/john/DATA		ext3	defaults	0	0
#/dev/sda1	/media/Windows		ntfs	defaults	0	0
/dev/sda2	/home/john/DATA/Temp	ext3	defaults	0	0
```

As far as I can see, it should work and sometimes it does.

BUT, every so often, I boot and my DATA partition won't mount. I look at GParted and see that my SATA drive has become 'sda' and my IDE is 'sdb'.

I edit my fstab file accordingly and reboot and it works..... Until next time after a few boots and I have the same problem. Looking at GParted I see that the SATA drive is 'sdb' again.

So for some reason by sda and sdb keep swapping over and I don't know why!

---

### Post by rapiscan on 2008-02-24
You can mount by UUID, as this doesn't change.

To find the UUID: ```
blkid
```

In your fstab:
```
 UUID=PUT_UID_HERE      /mount/here     ext3    defaults         0       0
```

---

### Post by Twizzle on 2008-02-24
I will try that - thanks.

---

### Post by laidback on 2008-02-24
I have found that Linux doesn't like the jumpers on the rear of the drives set to Cable select...it prefers master and slave. Worth checking.

---

### Post by Twizzle on 2008-02-25
I have tried the UUID option and it seems to work for now but I will see after a couple of reboots.

As for the jumpers, my IDE drive is set to cable select so if it still plays up, I will try that too.

Thanks for your help.

---

