---
title: "Drive access a stupid question"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by SVwanders on 2006-03-16
Okay, I know this seems like a stupid question and is probably so simple that I will shoot myself for asking it but I have two drives on this machine. How to I access that other drive. It is setup using FAT32. I got to Computer File browser but don't see any of those files. I know at boot up the two drives are set up. How do I gain access to my other drive . . . and what is that second drive call in Linux? It is simply a device?

Tim

---

### Post by mlind on 2006-03-16
You need to mount that drive.

```

sudo fdisk -l

```

will display you all available partitions and their filesystem types.
see wiki thread [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by pbaehr on 2006-03-16
You need to mount the other drive. It is, like you say, simply a device. Assuming you have Ubuntu installed on your first hard drive (primary master) it resides on hda. The other drive would be hdb. Again assuming that you have only one partition per drive Ubuntu is more specifically located at hda1 (first hard drive, first partition) and your fat32 drive would be located at hdb1 (second hard drive, first partition).

Finally, assuming that my assumptions are correct (is that some kind of recursive assumption?) in order to mount your second hard drive you would first create a mount point (let's say fat32 under media) by typing
```
sudo mkdir /media/fat32
```
That creates a directory where the files will later show up.
Then you mount the drive using
```
sudo mount -t vfat /dev/hdb1 /media/fat32
```
That basically tells the computer that you have a fat32 (vfat) formatted hard drive located at /dev/hdb1 and you want to mount it at /media/fat32.
Now the files should show up when you open /media/fat32.

You can make the computer mount the hard drive everytime it boots by adding an entry to /etc/fstab. There is a very good guide for that somewhere...I'll see if I can find it and post again.

Edit: Here's the guide I used to get started with fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by aysiu on 2006-03-16
These tutorials may help.

Abbreviated:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

Expanded:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by SVwanders on 2006-03-16
That did it! Many thanks . . . the new file has the contents of the other drive. This is cool. Thanks for the help.
:D 

Tim

---

