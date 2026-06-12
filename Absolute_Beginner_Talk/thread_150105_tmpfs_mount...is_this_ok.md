---
title: "tmpfs mount...is this ok ?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by infoseeker on 2006-03-25
I get this :
> $df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc2              16G  3.0G   12G  21% /
tmpfs                 245M     0  245M   0% /dev/shm
tmpfs                 245M   13M  233M   6% /lib/modules/2.6.12-10-386/volatile


The second entry .. is it ok to leave as is ?

Thanks

---

### Post by tkiesel on 2006-03-25
Looks just fine to me. :)

Mine is...

```
tkiesel@gecko:~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdd2             6.6G  3.5G  3.1G  54% /
tmpfs                 507M  4.0K  507M   1% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-k7/volatile
/dev/hdd3              69G   36G   34G  52% /home
/dev/hda1              39G   35G  3.8G  91% /mnt/windows
//jukebox/music        67G  8.7G   59G  13% /mnt/jukebox_music
//jukebox/movies       67G  8.7G   59G  13% /mnt/jukebox_movies

```

From what I understand, the tempfs on /dev/shm and/or /lib/modules/XYZ/volatile is your virtual memory swap area. It's a good thing. :)

---

