---
title: "External Hard Drive with no permissions, cuz of previous linux installation"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by gryzzly on 2007-12-18
Hi guys, just got my new laptop and bought also mobile rack, to use old hard disk from old PC. So, it was an ubuntu installation on it, and it is two partitions ext3, one "/" and one "/home" - i would like to reformat that drive (which is on usb mobile rack) and make it one big partition, cuz i am going to use it just as a storage for data.
Problem is, that GParted doesn't allow me to do anything with that disk, cuz probably i don't have permissions from this installation to change anything there. I know password of the user and i know everything about that installation i had there, but what i can do from here, from new installation?

Is it any bash command that i could use to change the permissions there?

so, /dev/sdb1 is one of partions, /dev/sdb3 is sekond, /dev/sdb2 - is swap, with which i can do whatever i want (delete, change)

tryed to use this:
```
sudo chown -R misha /dev/sdb1
```
it just did it, without any error, but didnt help;

this also didn't help:
```
sudo chmod -R 777 /dev/sdb1
```

and same operations with /dev/sdb (which is hard disk itself) also didnt help;

can anybody help?

---

### Post by gilf on 2007-12-18
I would think gparted would overide permissions on an external disk.

Partitions have to be unmounted if I remember correctly, first.

Are you using gparted correctly?

You would first have to delete partitions before formatting them.

And generally you should make the changes one at a time and then save them.

Also What user is running gparted?

---

### Post by pjkoczan on 2007-12-18
You shouldn't be trying to chown or chmod a disk device directly. It can cause weird behavior and won't work for what you want to do.

It sounds like what you want to do is repartition and reformat the disk. BE CAREFUL when you do this so you don't lose necessary data.

First, to re-partition (you can also use parted/gparted, but I'm not familiar with them):

```

sudo fdisk /dev/sdb

```

Delete the current partitions, add one partition that's the size of the entire disk, save the partition table, and exit (the commands to do that are in fdisk docs and help screens, you should be able to figure them out).

You can confirm that this worked by running:

```

$ ls /dev/sdb*

```

Only /dev/sdb (the disk itself) and /dev/sdb1 (the partition) should show up.

Next, reformat the newly created partition (/dev/sdb1). You can use the mkfs command, and there are possibly some graphical tools I'm not familiar with that may work better for you. I'm not going to give you exact syntax since it's a command that you should look up and understand before running.

Finally, you'll have to "mount" the filesystem at a directory (aka mount point) to see the data on the disk.

For instance (if you want to mount the disk at the  /mnt/otherdisk directory):
```

sudo mount /dev/sdb1 /mnt/otherdisk

```

and then all the data on that disk will show up under /mnt/otherdisk.

Note that, when you reboot, the mount point will be lost, unless you create an entry for it in /etc/fstab. There are many resources online (for example, [http://www.comptechdoc.org/os/linux/manual1/mountpoints.html](http://www.comptechdoc.org/os/linux/manual1/mountpoints.html)) in case you need to look something up.

I know this is a lot of info to swallow, but I hope it helps. Let us know if you get caught up anywhere in the process. Best of luck.

---

### Post by bcrom on 2007-12-18
It's very strange that GParted won't reformat the disk.  Crazy idea: try booting from the liveCD and using Gparted there.  If that doesn't work, there's something wrong with the drive.

---

### Post by gilf on 2007-12-19
Yup, the command line example given earlier should do it, but I'm also curious about why gparted wouldn't.

Did you enter gparted as superuser?

gksudo gparted

And then did you switch to the proper drive? (it may not be the only serial drive on your system)

Remember it must be unmounted first, too.

I'm pretty sure I've re-formatted previously used usb drives with gparted.

It couldn't be something weird like the gparted you opened resides on the external, or even worse, you booted off of the external, could it? I suppose a grub entry could place the external high on the list if connected or something. 

You definitely couldn't unmount it if either of these is true.

---

### Post by psusi on 2007-12-19
gparted will work just fine as long as the drive isn't mounted.

---

### Post by bcrom on 2007-12-19
That's true.  I had the same problem with gparted.  Be sure you type 
```
sudo umount -a
```
before you try to run gparted.

---

### Post by gryzzly on 2007-12-21
Thanks guys, after i deleted the partitions with fdisk thru terminal, gparted did its work

---

