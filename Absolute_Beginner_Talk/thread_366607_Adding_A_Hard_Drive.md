---
title: "Adding A Hard Drive"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by butterball on 2007-02-21
*first off, i'd like to let you know that i'm new to both forums and ubuntu.

I installed ubuntu on the hard drive that i've always used for my windows os. i totally erased it beforehand and everything works fine. i also have an 80GB drive that i use for all of my file storage. This hard drive is regularly transferred between my two computers. The format is NTFS. I have a few questions about this:
-Is there a format i can use to transfer this hard drive from a Windows run computer to the Ubuntu run computer without having to change any settings whenever I do?

-How do I mount the hard drive in Ubuntu? It's not shown in computer and device manager says the ignore paramater is "true"

---

### Post by indytim on 2007-02-21
FAT32 is the default common format between the Windows & Linux.  Be aware that there are size limitations on files for FAT32 (~4.0G).  It has been posted on these forums that there are driver(s) available to enable Windows to access ext2.  There are also some experimental work being done on the K-Uubuntu side to enable write access to NTFS formatted partitions.

Samba is a commonizer for reading data into a Windows environment from a Linux server.

Hope this helps.

IndyTim

---

### Post by butterball on 2007-02-21
thanx much. know anything about my mounting problem?

---

### Post by indytim on 2007-02-21
Have you partitioned and formatted the new HD yet (sorry for the delay as I'm now @work on my Win2k ops)?

IndyTim

---

### Post by anaconda on 2007-02-21
Is it an USB hd or just normal hd, which you connect to your computer?

USB hd should be found automatically.

With normal hd you either have to mount it manually or add it to your /etc/fstab -file so that it will be mounted automagically.

One way to mount it manually is to type to terminal

```
sudo mkdir /storage:
sudo mount -t ntfs /dev/XXX /storage  
```
the mkdir command creates a new directory, where you will mount your hd and the mount command will mount it to that directory. (if you mount it to /media/whatever , then the icon will come also to the desktop)

Here you have to change the XXX to the name of the partition. 
```
sudo fdisk -l
```
will tell you which partititon is which.
SATA disks are named sda1, sdb1, sdc1 ..etc
and IDE disks are named hda1, hdb1, hdc1.. etc
(the 1 is the first partition 2 second etc..)

---

### Post by Ben Sprinkle on 2007-02-21
I mount my ntfs with this:
```

sudo mount /dev/sda1 /media/sda1
```

---

