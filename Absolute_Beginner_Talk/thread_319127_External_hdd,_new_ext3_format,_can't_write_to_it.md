---
title: "External hdd, new ext3 format, can't write to it?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by linuxa on 2006-12-15
Hi there

I got myself a new USB 100GB Seagate external harddrive (2.5 inch, looks very nifty :D).

Having partitioned and formatted it as ext3 in QTParted.

I'm finding that I don't have any write access to the drive unless I first go:

```
sudo chown <username>:<username> //media/sda1
```

<username> is the name I log in with.

So two questions if you will:
1) Why would I have to manually change the owner permission to start using this device, all of the other devices in //media are owned by root and I (presumably) could write to them - haven't had to do this for my usb flash pen for example.

2) The command above is only effective if I use **//media/sda1**, doesn't seem to work if I use **/dev/sda1**. Why is that?

Thanks in advance all.

---

### Post by steve.horsley on 2006-12-15
1) 
I suspect that all the other devices in /media are FAT. FAT filesystem is incapable of storing user and group permissions (a unix concept) and so you have to set a default permission which applies to every file and directory on the partition. This is specified in "umask=???" in the mount command (or fstab). On the other hand, ext3 does of course store user and group permissions, and these are used in the normal fashion.

2)
/media/sda1 is the mount point, the directory at which the partition is hooked into the file system. This is where you should be setting the file ownerships. /dev/sda1 is the block device that is used by the driver when reading/writing the partition, and permission to read/write that device has no bearing on what permissions are stored against individual files in the filesystem on that partition. I believe that the device should read/write only by user root and group disk.

---

### Post by linuxa on 2006-12-15
Than you **steve**, that was a very detailed and thorough reply.

It did infact further my understanding by quite a bit.

Though I could understand that Unix uses permissions to allow/restrict user and group access. What I still don't get is why the default permission on my //media/sda1 is set to root when I formatted it using QTParted logged in as my own username.

---

### Post by Bachstelze on 2006-12-15
Firstly, you should use **/media/sda1** and not **//media/sda1**.
Secondly, if I were you, I'd format it as ext2, not ext3. The journaling can cause problems on removeble drives.
Thirdly, QtParted is always run with root privileges, or you wouldn't be able to do anything in it.

When you CHMOD /media/sda1, are the perms reset when you unplug/replug the drive or when you format it ?

---

### Post by steve.horsley on 2006-12-15
As HymnToLife said.
You cannot have formatted /media/sda1 as your normal user because normal users are not allowed to run QTparted. You must have used sudo (or better, gksudo) to run it, in which case you were running it as root, not as yourself.

sudo and gksudo allow you to run a program as a different user. The most common use is to run commands that need extra privilege as root.

---

### Post by linuxa on 2006-12-16
Thanks for the info guys & gals :D

I seem to have lost the reply that I posted to **HymeToLife** yesterday (hopefully it didn't end up in another thread :p)

Given that fact that repartition and reformatting is done via the root account, I now understand that there's a need to change ownership after each of those operations.

Can you guys further elaborate as to why ext3 isn't a good file system to use for external harddrives? I need to know having spent more than an hour backing up 5 GB of data (USB1.1 - computer limitation, nothing to do with external hdd).

Journaling is the feature used to prevent file fragmentation right?

---

### Post by steve.horsley on 2006-12-16
HymnToLife said that journalling can give problems to external drives. I have no idea why, and in fact I use reiserfs on my 80G external USB drive. I haven't had any problems.

Journalling is where the computer notes on the disk in the journal what it is going to do before making any changes to the disk filesystem. That way, if power is lost in the middle of an operation, it is possible to undo or complete the operation afterwards rather than leaving the filesystem in an inconsistent state. It removes the danger of the really scrambled filesystem where half the contents disappear because an inportant structure was half-written.

---

### Post by Bachstelze on 2006-12-16
Oh never mind, I thought it was a Flash drive, not a HD...

For information, Flash memory has a limited number of read/write cycles. So given that the journaling requires data to be written twice, it can virtually divide by two the drive lifetime.

---

### Post by steve.horsley on 2006-12-16
Ah. That explains it. Thanks.

---

### Post by linuxa on 2006-12-16
That does explain it.

Thanks so much for being so patient with me through this.

I'm pretty stoked that that harddrive is working now on Linux :D

Best Regards

---

