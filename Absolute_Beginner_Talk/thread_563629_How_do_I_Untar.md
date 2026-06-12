---
title: "How do I Untar"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-30
Hi this might seem like a strange and obvious question but I'm just worried about messing up my system. I followed[ this guide]("http://ubuntuforums.org/showthread.php?t=35087&highlight=samba") to backup my whole system with:
> tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/tmp /
I have got the archive I want and moved it to another partition that resides in > /media/Backup_200GB/Ubuntu_Server/backup.tgz
I now want to untar the file on that partition in the folder where it is. So I want the content of the tarball to be untared to /media/Backup_200GB/Ubuntu_Server/

Im asking because the guide says that I should be 100% sure of what im doing otherwise I will overwrite my current system.

---

### Post by kerry_s on 2007-09-30
cd /media/Backup_200GB/Ubuntu_Server <to get to the right place
ls <to make sure your in the right place
tar xzvf backup.tgz <to extract

---

### Post by kasperbs on 2007-09-30
thanks

---

