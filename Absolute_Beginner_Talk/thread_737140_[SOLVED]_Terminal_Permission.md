---
title: "[SOLVED] Terminal Permission"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by tranquito on 2008-03-27
Hi there. I'm not great at bash commands yet and I was wondering if anyone could help me out with this little issue.
All my music is backed up at /media/disk-2/backuphomemusic/Music on a different drive. The owner is root and there are no read write permissions for my normal user groups. How can I change ownership and permissions for everything on that drive without doing it manually one by one?

---

### Post by oedha on 2008-03-27
sudo chmod -R 777 /media/disk-2/backuphomemusic/Music
question : what is your drive partition table ? ext3 or NTFS ?

---

### Post by LowSky on 2008-03-27
yeah, that command wot work on a NTFS fomated drive

---

### Post by opscure on 2008-03-27
try:

```
sudo chown -v -R `whoami` /media/disk-2/backuphomemusic/Music/
```

then:

```
sudo chmod -R 777 /media/disk-2/backuphomemusic/Music
```


please post whatever errors you might get from the command line, so we can help you better.

---

### Post by aysiu on 2008-03-27
As others have hinted at, it greatly depends on what the filesystem is.

For Ext3:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

For NTFS or FAT32:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by tranquito on 2008-03-27
Thanks for your help. Its ext2. I did the chmod command suggested but that only changes the mode of the folder, not the entire directory contents. Any suggestions?

---

### Post by tranquito on 2008-03-28
chpwned!!! Ok the chown command worked the second time, i didn't add the other parameters the first time. Thx everyone.

---

