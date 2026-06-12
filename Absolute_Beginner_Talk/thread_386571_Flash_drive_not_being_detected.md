---
title: "Flash drive not being detected"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-03-17
I recently bought a 2GB Integral flash drive. I look at the instructions and it said it was compatible with the Linux kernel 2.6 or higher. When I put it in, nothing happened. I checked in Konqueror for signs of it existing but it wasn't there. Can anyone help me fix this? I'm using Kubuntu Edgy.

---

### Post by eljalill on 2007-03-17
My guess is, that you need to mount the drive. If you are not having any other flash drives pugged in, it should be sda1,
sou you could try open a terminal and type
```
sudo mkdir /media/Flashdrive
sudo mount /dev/sda1 /media/Flashdrive
```
Then you should find you flashdrive in /media/flashdrive...

Does that help?

---

### Post by miggols99 on 2007-03-17
I tried that and this is what came up:
```
michael@mike-and-harry:~$ sudo mkdir /media/flashdrive
michael@mike-and-harry:~$ sudo mount /dev/sda1 /media/flashdrive
mount: special device /dev/sda1 does not exist

```

---

### Post by eljalill on 2007-03-17
Well, I guess it is not called sda1 then....
Could you open a partition manager and find out there? You should be able to switch between looking at your internal hard drive and serial devices, which is how you could find out what it is actually called...
Or you could just try whether "sda" (without the 1) or "sdb" work, instead of "sda1"

---

### Post by miggols99 on 2007-03-17
It says it is sda but when I put that into the terminal
```
michael@mike-and-harry:~$ sudo mount /dev/sda /media/flashdrive
mount: /dev/sda is not a valid block device
```

---

### Post by eljalill on 2007-03-17
What is the output when you run 
fdisk -l 
in a terminal?

---

### Post by miggols99 on 2007-03-17
output of fdisk -l
```
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

```

---

### Post by eljalill on 2007-03-17
Hm. 
Have you formatted the flash disk? Do you know what filesystem it has?
You could check in the partition manager.

---

### Post by miggols99 on 2007-03-17
In the partitioner (KDE Control Module) one of them says Removable USB Disk. But there is no more information about it, except that it uses /dev/sda

---

### Post by eljalill on 2007-03-17
You could try to find out with fdisk:
sudo fdisk -l /dev/sda 
and see, whether that gets you anywhere...

But in case you don't have anything on it, I would advice formatting the device.
I am not quite sure, why it has problems with mounting, apparently it might have something to do with corrupted file system.

You should be able to format your device with the partitioner (right click on sda, you should find something like "format to" or so. Here you can shose a file system).

---

### Post by miggols99 on 2007-03-17
I don't think the program I am using is a partitioner. Could you recommend any partitioners for KDE?

---

### Post by eljalill on 2007-03-17
QTparted is supposed to be good...

---

### Post by pxwpxw on 2007-03-18
If you use a terminal, <parted> should be availabe for linux partitioning, and to see what you have: 
example:
```

max@ibook:~$ sudo parted /dev/sda print

Disk /dev/sda: 507MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End    Size   File system  Flags
 1      0.00kB  507MB  507MB  fat32

Information: Don't forget to update /etc/fstab, if necessary.

max@ibook:~$

```

Also 
```

ls -la /dev/sd*

```
to confirm what sd drives and partitions exist.

And for formatting the flash drive:
```

sudo mke2fs /dev/sda

```
for linux ext2/3 formatting 
or see <man mkfs> for other formats  

But make sure you dont format the wrong drive.

---

### Post by miggols99 on 2007-03-18
Ok it's working now. Thanks :)

---

