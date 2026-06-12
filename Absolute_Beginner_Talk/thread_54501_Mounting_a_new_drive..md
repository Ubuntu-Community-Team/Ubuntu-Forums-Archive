---
title: "Mounting a new drive."
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by fritogotlayed on 2005-08-04
Totally newb question here but I cant find what Im looking for out there on the net so I get to pick your brains.  The machine I am running ubuntu on right now has two hard drives in it.  During install ubuntu only installed itself on one.  When I open up / in the browser I only have 61Gb when with both drives I should have 100.  For some reason the hdb did not get mounted...  I was wondering how do I format the hdb to the native file format for ubuntu (ext2 I was told by one of my freebsd friends).  After that is done how do I mount the drive to the virtual file system.  Thanks much in advanced.  ~Matt

---

### Post by xmastree on 2005-08-05
[QUOTE=fritogotlayed]For some reason the hdb did not get mounted...  I was wondering how do I format the hdb to the native file format for ubuntu [/QUOTE]Try this:
```
sudo cfdisk /dev/hdb
``` 
> After that is done how do I mount the drive to the virtual file system.First you create a mount point somewhere, /mnt/disk2 for example. Just make a directory there. Then to mount it manually:```
sudo mount /dev/hdb1 /mnt/disk2
``` 
It's better to put it in your fstab so it will be mounted automatically on boot next time.

---

### Post by fritogotlayed on 2005-08-05
Thanks so much on the quick reply!  

root@FritoBoxUbuntu:/mnt # sudo cfdisk /dev/hdb
    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hdb5                    Logical   Linux                            40024.19*


root@FritoBoxUbuntu:/mnt # sudo mount /dev/hdb5 /mnt/disk2
mount: you must specify the filesystem type


root@FritoBoxUbuntu:/mnt # sudo mount -t ext2 /dev/hdb5 /mnt/disk2
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I got that far...  The cfdisk said the format was "Linux" if that helps any...  Also once this starts working where is the fstab located?  I really do appreciate the help!
~Matt

---

### Post by xmastree on 2005-08-05
> mount: wrong fs type, bad option, bad superblock on /dev/hdb5,Hmm... something not quite right there. I'm wondering why it's hdb5 not hdb1 though.

Perhaps someone more expert can help here...

> Also once this starts working where is the fstab located? You'll find it in /etc
```
sudo gedit /etc/fstab
```

---

### Post by xmastree on 2005-08-06
OK, because of my failure to answer that, I decided to try adding a second drive to this system. It's nothing important, so no bid deal if i break it...

This is what I did, all from within a root terminal.

# fdisk /dev/hdb

m	see commands
d	delete what's there
w	write and exit

# fdisk
n	new
p	primary
1
default first and last cylinders
w	write and exit

#fdisk
p	just to see its there
q	quit


# mkfs -t ext3 /dev/hdb1
(that's the equivalent of formatting your new partition in dos/Win)

#gedit /etc/fstab
add this line:
/dev/hdb1	/mnt/disk2	ext3	defaults	0	2
Save and exit.


# mount -a
This will try to mount all partitions in fstab which aren't currently mounted. like the one you just made. It should now be accessible, and automatically mounted at the next boot.


Worked for me. as presumably you haven't used that disk yet, there's nothing to lose **[COLOR=Red]providing you make sure you're dealing with hdb, not hda[/COLOR]**

---

### Post by Kapre on 2005-08-06
[QUOTE=xmastree]Hmm... something not quite right there. I'm wondering why it's hdb5 not hdb1 though.

Perhaps someone more expert can help here...

You'll find it in /etc
```
sudo gedit /etc/fstab
```[/QUOTE]
 
Quote:
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
Hmm... something not quite right there. I'm wondering why it's hdb5 not hdb1 though.

Seems like the hd has another partition...suggest running fdisk (windoze diskette) to check..

---

### Post by fritogotlayed on 2005-08-06
xmastree... you rock ;-)   thank you so much.  I appreciate all the help and you got major props from me :-D

---

### Post by xmastree on 2005-08-07
[QUOTE=fritogotlayed]xmastree... you rock ;-)   thank you so much.[/QUOTE]I guess this means you got it working?
Great.  :grin: 

Glad to help.

---

