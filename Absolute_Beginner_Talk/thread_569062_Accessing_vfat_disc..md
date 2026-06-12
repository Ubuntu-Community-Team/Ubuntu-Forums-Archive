---
title: "Accessing vfat disc."
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Osedax on 2007-10-06
Hello,
I've got a SATA hdd with one big vfat partition* on it that I created back when this machine was running windows. Now I'm running Dapper, which recognizes the disc and partition in Disk Manager, but lists it as "inaccessible", and does nothing when I hit enable. I've got a lot of files in the disc, so simply reformatting isn't an option. I modified fstab to list the drive, but that hasn't done anything. I've read some of the docs, but nothing seems to explain it.

*Dapper reads it as vfat, but when I originally formatted it, I set it to fat32.

---

### Post by taurus on 2007-10-06
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```
p.s.  Fat32 **is** vfat.

---

### Post by sidey1234 on 2007-10-06
no need for commands being pasted


just do 
mkdir /mnt/disk*
sudo mount -t vfat <path to disk**> /mnt/disk

*anything you want
** what your disk is actually read as ie /dev/sdb,c,d etc

then if you cd into /mnt/disk all your files

---

