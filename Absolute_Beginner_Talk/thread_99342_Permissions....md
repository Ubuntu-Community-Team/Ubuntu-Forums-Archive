---
title: "Permissions..."
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by REDISISTone.nl on 2005-12-05
Hi !!
A friend of mine (ubuntu_deamon) installed ubuntu for me. Now i'm trying to get azareus to work but it is not wrinting to my fat32 partition. So i made (gparted) a new partition to download to. I made a partition (ext3), did
```
sudo gedit /etc/fstab
```
and added this:
```
/dev/hda9       /media/hda9     ext3    nosuid,noexec   0       0
```
now i need to mount it but I just get this:
```
rnr@p3-rnr:~$ sudo mount /dev/hda9
mount: mount point /media/hda9 does not exist
```

sum1 got a idea what im doing wrong? (sorry 4 being n00b :confused: )

Thanx !!

---

### Post by invalid on 2005-12-05
```
sudo mkdir /media/hd9
```

---

### Post by atoponce on 2005-12-05
Writing to the NTFS partition is not enabled by default in the Linux kernel because of lack of support, a number of bugs and much more.  It doesn't matter how much you play with permissions, if it isn't compiled in the kernel, it aint happening.

Your best bet is to create a FAT32 partition that both Windows and Linux can recognize, read and write, and move your data there.

---

### Post by Gray. on 2005-12-05
try
**sudo mkdir /media/hda9**
then 
**mount /dev/hda9 /media/hda9**

though you might want to edit your /etc/fstab so that it says
**/dev/hda9           /media/torrents**
just make sure that you make the directory
(sudo mkdir /media/torrents)
and change the mount options appropriately
(sudo mount /dev/hda9 /media/torrents)

Just looks nicer that way. :P

---

### Post by REDISISTone.nl on 2005-12-05
[QUOTE=invalid]```
sudo mkdir /media/hd9
```[/QUOTE]

(u mean sudo mkdir /media/hda9)

Big thanx :)

---

### Post by invalid on 2005-12-05
[QUOTE=REDISISTone.nl](u mean sudo mkdir /media/hda9)

Big thanx :)[/QUOTE]
oops, typo! yes, hda9

Cheers,
Cb

---

