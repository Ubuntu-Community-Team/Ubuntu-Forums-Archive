---
title: "How can I see my other HD partitions?"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-10
Hello everybody.

I would like to see my other partitions through the Terminal.

I have 1 Hard Drive with 3 partitions:

1. My Ubuntu Partition
2. A second Partition - curently empty EXT3
3. A third Partition - formatted from Windows - a FAT32 one

I know how to become a superuser.

Where on the root can I see my above 3 partitions, as a list?

I went in "/dev", but could not find a clue...

Can anybody tell me where do I go & what do I type to see my Hard Drive Partitions?

My next step will be to be able to access them with the "mount" command, but first I need to locate them...

Thanks guys!!!

Dimitris.

---

### Post by drummer on 2006-02-10
```
sudo fdisk -l
``` is what you want.

---

### Post by dvarsam on 2006-02-10
I did what you suggested, and I got:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        6079    29294527+  83  Linux
/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)
/dev/sda5            6080       10011    31583758+   b  W95 FAT32
root@ubuntu:/#

What happened to "/dev/sda4"?

I know that I have 3 partitions, but why did it jump from sda3 to sda5?

---

### Post by dvarsam on 2006-02-10
At the same time I want to ask you:

How do I mount the "/dev/sda5" partition?

I created the folder:

                                        mkdir sda5

& then I typed:

                                        mount -t vfat /dev/hda5 /sda5

I get the following output:

                                        mount: /dev/hda5: can't read superblock

What am I doing wrong?

What do I have to type, for the icon to appear on the Desktop?

---

### Post by drummer on 2006-02-10
hmm... i don't have sda4 either, think it's something to do with having an extended partition. numbering is just different somehow. nevermind though, it's just a name. Here's my output:```
owen@breezybox:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 5129 MB, 5129671680 bytes
255 heads, 63 sectors/track, 623 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         593     4763241   83  Linux
/dev/hdc2             594         623      240975    5  Extended
/dev/hdc5             594         623      240943+  82  Linux swap / Solaris

Disk /dev/sda: 82.3 GB, 82347195904 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2            9824       10011     1510110    5  Extended
/dev/sda3             609        9823    74019487+  83  Linux
/dev/sda5            9824       10011     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by drummer on 2006-02-10
[quote=dvarsam]mount: /dev/hda5: can't read superblock[/quote]That's because you need to mount /dev/**s**da5, instead of /dev/hda5. ie. ```
mount -t vfat /dev/sda5 /sda5
```

/dev/hda would be the name of the first IDE device on a system, where /dev/sda is the first sata or scsi device. As you can see in my post above, /dev/hdc is my ide drive (master on the 2nd ide bus) and /dev/sda is my sata drive.
hda is the name for a device on - 1st ide bus, master
hdb - 1st ide bus, slave
hdc - 2nd ide bus, master
hdd - 2nd ide bus, slave
..... and so on
sda - 1st sata device
sdb - 2nd sata device
..... and so on, you get the idea...

---

