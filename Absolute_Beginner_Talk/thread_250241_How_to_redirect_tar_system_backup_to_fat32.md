---
title: "How to redirect tar system backup to fat32?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-09-03
Using
sudo su
cd /
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/home/drives --exclude=/home/orb/Movies /

which saves to root but I would like it to back up to

home/drives/hdd1/Ubuntu-Configs/Sys-Backups

my fstab is /dev/hdd1       /home/drives/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       0

Just can't seem to fiqure out what is wrong works fine for creating a backup in /

Any help is greatlly appreciated.

---

### Post by orb9220 on 2006-09-03
bumpity bump

---

### Post by Miademora on 2006-09-04
How about this one?

```
tar cvpzf /home/drives/hdd1/Ubuntu-Configs/Sys-Backups/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/home/drives --exclude=/home/orb/Movies /
```

Please include any errormessages if you get one.

---

