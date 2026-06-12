---
title: "HDD wont mount"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by RedGreen on 2007-09-13
I have a second internal hard drive that when I installed a few days ago would let me read from (but not write to) but now it recognizes it but says I am not privileged to mount the volume. It is formatted in NTFS. Any help on getting it to mount and be read/writeable would be greatly appreciated.

---

### Post by alienexplorers on 2007-09-13
Try
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by benerivo on 2007-09-13
I would put an entry for it in /etc/fstab that reads...```
# /dev/hdb
UUID=TEDC342FDC7194F7 /mnt/Storage ntfs-3g gid=1000 0 0
```
This assumes that you have the ntfs-3g package installed. You would need to replace the UUID string (TEDC342FDC7194F7 ) with the one for your drive. You can find out what it is by looking in /dev/disk/by-uuid and checking the properties to see which one is the ntfs drive you are interested in. For this example, you would also need to create a folder in /mnt called Storage.

---

### Post by RedGreen on 2007-09-13
> **alienexplorers said:**
> Try

using the command

> blkid

I can find the HDD im trying to mount:

> /dev/sda5: UUID="01286099-5a51-4bd0-b503-83344cda689b" TYPE="swap" 
/dev/hdc4: TYPE="ntfs"

Although im still at a bit of a loss of how to go about mounting it. Its NTFS.

---

### Post by eduardounder on 2007-09-13
Seeing what your posted up, YOUR_HD should be = hdc4

First install ntfs-3g and ntfs-config tool
Also make the HD entry point
> 
sudo apt-get install ntfs-config
sudo mkdir /media/YOUR_HD


Edit the fstab (so it can be mounted more easily, and auto)
> 
sudo gedit /etc/fstab

Now add a new line at the end and put
> 
/dev/YOUR_HD /media/YOUR_HD ntfs-3g defaults 0 1

Close it,
Then..
> 
sudo ntfs-config

In the ntfs-config, Enable input and output for writing

Now reboot, and see if everthing is working fine..

---

### Post by RedGreen on 2007-09-13
> **benerivo said:**
> I would put an entry for it in /etc/fstab that reads...```
# /dev/hdb
UUID=TEDC342FDC7194F7 /mnt/Storage ntfs-3g gid=1000 0 0
```
This assumes that you have the ntfs-3g package installed. You would need to replace the UUID string (TEDC342FDC7194F7 ) with the one for your drive. You can find out what it is by looking in /dev/disk/by-uuid and checking the properties to see which one is the ntfs drive you are interested in. For this example, you would also need to create a folder in /mnt called Storage.

I have ntfs-3g. Using the UUID that "blkid" gives me I get this:

> # /dev/hdb
UUID=01286099-5a51-4bd0-b503-83344cda689b /mnt/Storage ntfs-3g gid=1000 0 0
bash: /mnt/Storage: No such file or directory

but in the properties menu of the drive I get a different UUID but the same result:

> # /dev/hdb
UUID=7CE45FC8E45F82F6 /mnt/Storage ntfs-3g gid=1000 0 0
bash: /mnt/Storage: No such file or directory

What am I doing wrong?

---

### Post by RedGreen on 2007-09-13
> **eduardounder said:**
> Seeing what your posted up, YOUR_HD should be = hdc4

First install ntfs-3g and ntfs-config tool
Also make the HD entry point


Edit the fstab (so it can be mounted more easily, and auto)

Now add a new line at the end and put

Close it,
Then..

In the ntfs-config, Enable input and output for writing

Now reboot, and see if everthing is working fine..

I did as you instructed although when I get the option to enable reading and writing the boxes are already checked and I still get the message that I do not have permission to mount the drive.

edit: sorry about the double post

---

### Post by benerivo on 2007-09-13
You need to make a directory in /mnt,  which is where the contents of the drive will be displayed. It will have to match whatever it is in fstab (in this case Storage). To make the new directory, open a terminal and type ```
sudo nautilus
``` and navigate to /mnt and make a new folder called Storage. Then edit /etc/fstab by opening it from the same file browser and entering the lines i mentioned above. Then reboot.

---

### Post by bodhi.zazen on 2007-09-13
In uUbuntu the "standard" mount point is /media, but you can mount in /mnt if you like.

From your error message I am gussing you need to make a mount popint.

```
sudo mkdir /mnt/Storage
```

Then re-try mounting ...

---

### Post by RedGreen on 2007-09-13
> **benerivo said:**
> You need to make a directory in /mnt,  which is where the contents of the drive will be displayed. It will have to match whatever it is in fstab (in this case Storage). To make the new directory, open a terminal and type ```
sudo nautilus
``` and navigate to /mnt and make a new folder called Storage. Then edit /etc/fstab by opening it from the same file browser and entering the lines i mentioned above. Then reboot.
I made the folder called Storage. Added the line to fstab

> /dev/hdc4 /media/hdc4 ntfs-3g defaults 0 1

then rebooted but nothing has changed.

> **bodhi.zazen said:**
> In uUbuntu the "standard" mount point is /media, but you can mount in /mnt if you like.

From your error message I am gussing you need to make a mount popint.

```
sudo mkdir /mnt/Storage
```

Then re-try mounting ...

when I try that code I get this message:

> mkdir: cannot create directory `/mnt/Storage': File exists

Now im confused at which point in all these steps am I actually trying to mount the drive.

---

### Post by stinger30au on 2007-09-13
try this, worked for me

[http://ubuntuforums.org/showthread.php?t=529838](http://ubuntuforums.org/showthread.php?t=529838)

---

### Post by bodhi.zazen on 2007-09-13
Hmmm, it seems you are getting all jumbled up ...

Mounting is not usually this hard ...

1. make a mount point

2. mount a partition to the mount point.

which partition are you trying to mount where ???

You can list your partitions with :```
blkid
``` OR ```
sudo fdisk -l
```

As far as mount point you have listed both /mnt/Storage and /media/hdc4  ???

========

Assuming you are trying to mount /dev/hdc4 to /mnt/Storage, 

what is the output of :

```
sudo mount -t ntfs-3g /dev/hdc4 /mnt/Storage
```

---

