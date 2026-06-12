---
title: "Maxtor-not a block device"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by sciencectn on 2008-01-28
I have this external USB Maxtor hard drive. It contains lots of valuable data so I can't reformat it, and it is not working with Ubuntu. I just tried it with a windows computer and it worked fine. I tried mounting it in a terminal by running dmesg to find the device was /dev/sg7, and I tried mounting it. Here's what happened:

```
chris@chris-desktop:~$ sudo mkdir /media/maxtor
chris@chris-desktop:~$ sudo mount /dev/sg7 /media/maxtor
mount: /dev/sg7 is not a block device
chris@chris-desktop:~$ 

```

So, I suddenly had the bright idea of running gparted and seeing what it says about the device. It displays that it's /dev/sdf1 on one partition and that the filesystem is unkown. There is another partition which is unallocated. 

I'm out of ideas. Is there any way of mounting this drive under ubuntu?

---

### Post by brettg on 2008-01-29
I see this post has been unanswered for some time now. Unfortunately I don't have an definitive  answer for you.

In theory it should "just work"

Some questions: What filesystem does it use? What capacity does it have? 

Do you have another (spare) hard drive that you could perhaps stick in the drive enclosure and see if Ubuntu can see that drive? This will narrow the problem down to either an interfacing problem or a FS format problem. 

If it is a reasonably small HDD, you might want to consider backing it up to another machine and then reformatting it. This requires that you have an appropriate machine available of course.

 Sorry I couldn't be of more assistance.

---

### Post by mikeyphi on 2008-01-29
> **sciencectn said:**
> I have this external USB Maxtor hard drive. It contains lots of valuable data so I can't reformat it, and it is not working with Ubuntu. I just tried it with a windows computer and it worked fine. I tried mounting it in a terminal by running dmesg to find the device was /dev/sg7, and I tried mounting it. Here's what happened:

```
chris@chris-desktop:~$ sudo mkdir /media/maxtor
chris@chris-desktop:~$ sudo mount /dev/sg7 /media/maxtor
mount: /dev/sg7 is not a block device
chris@chris-desktop:~$ 

```

So, I suddenly had the bright idea of running gparted and seeing what it says about the device. It displays that it's /dev/sdf1 on one partition and that the filesystem is unkown. There is another partition which is unallocated. 

I'm out of ideas. Is there any way of mounting this drive under ubuntu?

If gparted doesn't recognise the format - probably Ubuntu won't!
However try this; Install testdisk from Synaptic and see if it tells you the format type, with that info you/we might have further ideas!

sg7 doesn't seem correct but sdf1 does.......what message if you mount sdf1?

---

### Post by sciencectn on 2008-01-29
I'm guessing what's inside the enclosure is a simple SATA hard drive; however, if I remove the drive from the enclosure it will void the warranty and I wont be able to get a new one if I break it.

When I tried to mount /dev/sdf1 this time it said:
```
chris@chris-desktop:~$ sudo mount /dev/sdf1 /media/maxtor
mount: you must specify the filesystem type

```

Which is weird, because last time I tried mounting sdf1 it gave the "can't find in /etc/fstab or /etc/mtab" error message.


I tried testdisk, it recognized the drive, and chose the analyze option. Here's the first output:
```
Current partition structure:

     Partition                  Start        End    Size in sectors

check_FAT: Incorrect size of partition
 1 P FAT16 >32M               0   1  1 24790 254 63  398267352
 1 P FAT16 >32M               0   1  1 24790 254 63  398267352
No partition is bootable

```

I chose proceed, and got this

```
Disk /dev/sdf - 203 GB / 189 GiB - CHS 24792 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1 24791 254 63  398283417 [LOCAL DISK]

```

I chose the option to do a full scan and check for more partitions. After about 10 minutes, the output windows came up with the exact same thing as before:

```
TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdf - 203 GB / 189 GiB - CHS 24792 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1 24791 254 63  398283417 [LOCAL DISK]












Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 203 GB / 189 GiB

```

The "Structure OK" looks reassuring :knock on wood:. The hard drive also has a sc400 Firewire connector on the back, which I tried with the exact same results.

I also ran "dmesg | tail" and got "VFS: Can't find a valid FAT filesystem on dev sdf."

And now I have no idea what to do next.

---

