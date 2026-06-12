---
title: "Folder disappear after shutdown...."
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Chouca on 2006-12-01
Hi,

I  made a new folder "Pool"  /dev/Pool.

I mounted a partition with  /dev/Pool as mountpoint

I made this folder a Shared folder,everything works fine - I even can see it over my wireless LAN in my XP computer (sometimes...).

I shut down Ubuntu(6.06)...and when I start up again Pooooof

The Folder has disappeared :evil: 

I have tried both with terminal and Nautilus and with root rights - no  success.

Is there any "save config" command or any other secret trick I have not understood...???

Thanks

Martin

---

### Post by mushroom on 2006-12-01
It may be because you created it in "/dev/", try "/media/" instead.

---

### Post by lloyd_b on 2006-12-01
To clarify mushroom's response....

In recent versions of the Linux kernel, the "/dev" directory is NOT a normal directory - it's actually the mount point for a special type of file system.  This file system is basically a ram disk with special features.  And like a ram disk, whenever you turn the machine off, anything that you've created in that file system is lost.

Some other "special" directories exist, with similar properties:
"/proc"
"/var/run"
"/var/lock"
"/sys"

Generally, underneath "/media" is considered the "correct" place for mounting a new file system.

Lloyd B.

---

### Post by Chouca on 2006-12-02
Thanks,

now the directories show up under /media   but...now the mounted partition disappears at shutdown....:-? 

I try to mount :
```

martin@ubuntu:~$ sudo mount /dev/hda3 /media/Pool

```

the partition is mounted OK I can add files into it I even managed to set permissions (:p )

I power off and abrakadabra after power up again no mounted partition - only the directory remains, i can not see any files in there...

Martin

---

### Post by Chouca on 2006-12-02
Found the solution to my problem by adding the following lines to /etc/fstab my partitions now mount and show up in a proper way;

```
/dev/hda3       /media/Pool     ext2    defaults,errors=remount-ro 0       1
/dev/hda5       /media/Pool2    ext2    defaults,errors=remount-ro 0       1
/dev/hda1       /media/Pool3    ext2    defaults,errors=remount-ro 0       1
```

Dont really understand what it means but it works...

:p   Yes!!!


Martin

---

