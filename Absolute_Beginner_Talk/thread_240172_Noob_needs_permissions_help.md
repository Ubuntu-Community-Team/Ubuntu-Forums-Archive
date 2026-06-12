---
title: "Noob needs permissions help"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by fatdawg on 2006-08-20
Hi, I have all my data on a seperate disc, hdb1, also called data. The permissions are set to read only. I have tried chmod ugo+rwx hd1 but "hdb1" is not recognised. Have tried "hdb 1" and "hdb1/data" and "data", but nothing.
The terminal line is:fatmatt@fatmatt-desktop:~$
I don't know if this is stopping me copy/pasting into terminal, which I can't do for various things inc Easyubuntu.
Dual booting with XP pro, Sempron 3000+, 1Gb ram
Thanks.
(PS:Really good idea to havea noobs section..)

---

### Post by noof on 2006-08-20
Have you mounted the disk? Like:```
sudo mkdir /home/data
sudo mount /dev/hdb1 /home/data
```

---

### Post by taurus on 2006-08-20
If it's NTFS, then you can only read from it but if it's fat32/vfat, then you can read and write to it.  You can set all that in /etc/fstab, NOT chmod...

You can edit your /etc/fstab with

```
gksudo gedit /etc/fstab
```
For NTFS filesystem, add this line to the end of it, /etc/fstab...

```

/dev/hdb1   /media/storage   ntfs   defaults,umask=0222   0   0

```
For fat32 filesystem, add this line to the end of it, /etc/fstab...

```

/dev/hdb1   /media/storage   vfat   defaults,umask=0000   0   0

```
Then at the prompt, type

```
sudo mkdir /media/storage
```
Reboot and you are ready to go...

---

### Post by fatdawg on 2006-08-20
Entering both commands gets "command not found"
(I am entering password as sudo requests)

---

### Post by noof on 2006-08-20
What happens if you type ```
which sudo
```

---

### Post by fatdawg on 2006-08-20
/usr/bin/sudo

---

### Post by taurus on 2006-08-20
Why don't you try out the steps in my post!!!  :rolleyes:

---

### Post by noof on 2006-08-20
Then you're doing something wrong :P ```
sudo mkdir /home/data
```should create a /home/data directory and
```
sudo mount /dev/hdb1 /home/data
``` should mount the disk.

Btw, do you have any directory named "hdb1" in /media ? Ubuntu detects my ntfs-partitions/disk automatically.

---

### Post by fatdawg on 2006-08-20
Taurus: after the second line, using nfts, I get
gedit/etc/fstab/dev/hdb1: command not found. 

Noob, after the second line I get:
mount: /dev/hdb1 already mounted on /home/data busy
mount: according to mtab, /dev/hdb1 is mounted on media/hdb1

---

### Post by fatdawg on 2006-08-20
Hey,did I do something to offend? Is anyone there? Please?

---

### Post by noof on 2006-08-21
> **fatdawg said:**
> Taurus: after the second line, using nfts, I get
gedit/etc/fstab/dev/hdb1: command not found. 

Noob, after the second line I get:
mount: /dev/hdb1 already mounted on /home/data busy
mount: according to mtab, /dev/hdb1 is mounted on media/hdb1Then try and browse to /media/hdb1. It seems like it already have found your disk. You should be able to read from it without problems.

---

