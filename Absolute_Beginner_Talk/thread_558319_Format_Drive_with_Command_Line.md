---
title: "Format Drive with Command Line"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-09-23
The 80GB drive use to be NTFS I think, it had Windows XP I think. I remember it had problems but I narrowed that down to the motherboard. I have it in my Ubuntu server, df -h shows the following:
```

kavon@ubuntu-server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   11G  6.5G  63% /
varrun                 30M   40K   30M   1% /var/run
varlock                30M     0   30M   0% /var/lock
procbususb             30M   68K   30M   1% /proc/bus/usb
udev                   30M   68K   30M   1% /dev
devshm                 30M     0   30M   0% /dev/shm
```

It doesn't seem to show up there. Help :(

---

### Post by Happy_Man on 2007-09-23
Do you have it mounted? "df" only shows mounted partitions, I think.

---

