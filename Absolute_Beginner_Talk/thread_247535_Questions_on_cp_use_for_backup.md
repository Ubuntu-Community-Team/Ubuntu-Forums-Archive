---
title: "Questions on cp use for backup"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-08-30
sudo su
cd /
tar cvpzf backup.tgz 
--exclude=/proc --exclude=/lost+found--exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/home/drives --exclude=/home/orb/Movies /

created a 1.2GB tarball what I wanted to know since my /home partion is on a different partition than root did it backup all the files there?

/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2

When I restore how does it restore files automatically to hda2 and hda4?

also would like to backup to a fat32 partition 

/dev/hdd1       /home/drives/hdd1     vfat    defaults,utf8,umask=007,gid=46 0       0

with the path /home/drives/hdd1/Ubuntu-Configs/Sys-Backups if I replace / with this path will it work. Had problems with errors along the lines of couldn't preserve file permissions. But wasn't sure that I was running a sudo su term at the time.

And info thread available for creating a script that I could exec when the need arises? Or just a point to detailed instructions to backup a system except for rsync which dosn't do fat32?

Any Help is always appreciated. As always ubuntu forum people most helpful that I have experienced anywhere else.

---

### Post by AntiFlash on 2006-08-30
if you're a seedling...i'm probably still in the pod.  i'm not too familiar with backups, but you should be able to browse your backup from within ark to see everything that it captured/didn't.  

you should be able to write a simple shell script that you can either introduce into your boot up cycle or set to run at some set frequency using "cron".   there are quite a few online tutorials on how to write shell scripts...

[www.tldp.org](www.tldp.org)

[http://www.tldp.org/LDP/abs/html/index.html](http://www.tldp.org/LDP/abs/html/index.html)

---

### Post by orb9220 on 2006-08-30
Thanks for the info.

---

### Post by orb9220 on 2006-08-31
bump

---

### Post by orb9220 on 2006-09-01
Any help appreciated.

---

