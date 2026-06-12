---
title: "Unmounting Partitions"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by xkcd on 2007-05-26
Ok, I'm almost through with the installation, but when I get ready to do the real install, a message pops up that says:

```
The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/The\040Abyss

Please close any applications using these mount points.
```

BTW The Abyss is the name of the partition.

I'm kinda lost at this point. Anybody know how to fix this problem? Many thanks.

---

### Post by Happy_Man on 2007-05-26
Do you have something open that is using files off that partition? If so, it won't unmount.

---

### Post by xkcd on 2007-05-26
That's my problem. I don't know what is running from that partition. Is there a way to check if anything from that partition is running?

---

### Post by taurus on 2007-05-26
Post the output of the last command here.

```
cd ~
df -h
```

---

### Post by xkcd on 2007-05-26
In the terminal it shows me a list of stuff, and on the bottom is the partition. What now?

---

### Post by xkcd on 2007-05-26
```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 248M   33M  215M  14% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 248M   33M  215M  14% /lib/modules/2.6.20-15-generic/volatile
varrun                248M  108K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
udev                  248M   88K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
tmpfs                 248M   20K  248M   1% /tmp
/dev/sda1             102G   26G   76G  26% /media/The Abyss
```


This is what comes up.

---

### Post by taurus on 2007-05-26
```
sudo umount /dev/sda1 
df -h
```

---

