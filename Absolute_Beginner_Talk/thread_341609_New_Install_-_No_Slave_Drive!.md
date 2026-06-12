---
title: "New Install - No Slave Drive!"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by brandknewme on 2007-01-18
Hello, first off, wow, I love Ubuntu, it's exactly what I needed in my life.

Now, my question is. 

I have set up XP and Ubuntu to dual boot.

When I was installing Ubuntu, I wasn't quite sure how it would happen and I was unsure if I'd lose my information, so when I was on step 4/5 I unchecked my 200gb  slave drive, that contained all my music, pictures and important information from the list and left it blank.

Now, I can't access it. I can only see my other 3 partitions I have set up, and my 200gb slave drive is nowhere to be seen. 

How can I add it safely?

please help!!
Thanks.

---

### Post by kebes on 2007-01-18
First off: welcome to Ubuntu. I'm glad you're enjoying it so far!


Yes, you can certainly mount your Windows drive in Linux. There are many different ways of doing it. First off, you should know that a Windows XP drive is formatted as "NTFS"... and Linux can read NTFS no problem, but the writing support to NTFS partitions is currently considered "experimental." Most people say they have not had problems... but some people have reported losing data.

So be warned that if you're saying things from Linux onto the NTFS partition, you may experience problems.


But enough of the warnings. How to mount the drive? Well if you're willing to delve into the "terminal" (Applications > Accessories > Terminal), then you can do it as described in this guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

It describes what to do. That guide assumes you know what partition is your Windows one. In Linux terminology it will be "/dev/hdb1" or something like that. If you run into problems, just post again with an explanation of the difficulties.


EDIT: I removed my suggestion for "disks-admin" because it seems not to be in the current repositories... anyone know how to graphically mount a partition in Gnome?

---

### Post by brandknewme on 2007-01-18
Hmm, I can't seem to find disks-admin. I did what you said. Nothing listed in there.

I have found my 200gb slave in the device manager. But, I don't know what to do from there.

---

### Post by kebes on 2007-01-18
Sorry about that ... I edited my post because I did a search of the repositories and it looks like "disks-admin" has been retired...

You could try running the program "gparted" (do Alt+F2 for the run dialog, type gparted and click Run). That program can format and manage partitions... I believe it also has the ability to designate mountpoints. At the very least you can use gparted to figure out what the Linux designation for your partitions are... which will make it relatively easy to mount the drive on the commandline if you want to.

Hope that helps.

---

### Post by brandknewme on 2007-01-18
My slave shows up as /dev/hdd1??

I am still not having any luck.

---

### Post by confused57 on 2007-01-19
Here's an excellent link for mounting drive partitions:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

This webpage also links to Aysiu's tutorial for mounting, which you might want to read.

Read the above for mounting instructions...but I'll give you a quick summary:

Boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

Make a note of your slave drive partition designation in Linux(hdb1, hdd1, etc)

You'll need to make a directory in Ubuntu to mount your slave drive:
```
sudo mkdir /media/data
```

then mount the slave drive partition, for ntfs:
```
sudo mount /dev/hdd1 /media/data -t ntfs -o nls=utf8,umask=0222
```

Then open Nautilus file browser and navigate to the media folder, there should be a "data" directory listed there that you can open and access your slave drive.
To unmount the slave drive partition:
```
sudo umount /media/data/
```

To have your slave drive partition mounted when you boot Ubuntu, you'll need to add an entry to your fstab, open a terminal:
```
 sudo cp /etc/fstab /etc/fstab_backup
```
this will create a backup file, to edit fstab:
```
gksudo gedit /etc/fstab
```

then add a line in fstab similar to this:
```
 /dev/hdd1     /media/data   ntfs  nls=utf8,umask=0222      0       0
```

then:
```
sudo mount -a
```
to mount the partition or
reboot and there should be an icon on your desktop for accessing it.
I suggest you read and follow the directions in the link(s)...I just wanted to give you an overview for mounting your slave drive partition.  I'm no expert, but it'll give you an idea of what you need to do using the links I provided.  The mounting options will be different for a FAT32 or Linux partition.

---

