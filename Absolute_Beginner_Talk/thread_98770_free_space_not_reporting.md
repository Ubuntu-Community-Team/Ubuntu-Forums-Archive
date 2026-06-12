---
title: "free space not reporting"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by nallelcm on 2005-12-04
I even ran it df - h as root... doesnt show /dev/hda1  mounted  to / is
```
root@llama:/home/nallelcm# df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/sda1             153G  116G   38G  76% /media/storage
root@llama:/home/nallelcm#

```

Can anyone help me out?

---

### Post by doitashimashite on 2005-12-04
What do you see when you enter the command

mount

---

