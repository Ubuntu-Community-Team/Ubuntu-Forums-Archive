---
title: "my drives suddenly gone!!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-04-01
every thing was normal yesterday i just went to sleep and today when i booted i did not find my hard drives on my desktop !! even my CD driver don't work i tried to play  one of my audio CD it tells my Can't mount it?? so what actually happened i need some help please:(

---

### Post by angel_zone on 2008-04-01
i had duall boot ubuntu 7.10 with windows xp and i had 6 drives if that would help

---

### Post by angel_zone on 2008-04-01
i had typed the following command just to see if they are mounted or not 
gksudo gedit /etc/fstab 
and here are the outout
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda12
UUID=608930e5-41c6-489b-840a-69a5662c3392 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda11
UUID=7b0bb52b-c84b-461a-8425-edeb91c30379 /boot           ext3    defaults        0       2
# /dev/sda1
UUID=ECBB-D615  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=CEDB-0A62  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=16BD-BF23  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=5EA0-7444  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=47E6-1B25  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=8FCC-3652  /media/sda9     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda10
UUID=6329386b-6981-4c9f-8400-8d34f4baa4c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
any help would be great i tried searching the forums but i really don't get it.

---

### Post by angel_zone on 2008-04-01
hey guys i sent this today morning and still can't make it works!! when i'm trying to mount my drives via terminal it tells me /etc/mtab input/output error i tried to access that file but it was'n there and when i tried mkdir /etc/mtab it tells me the file already exist!! please anybody i really need help in this i can not simply re-install the whole system again

---

### Post by angel_zone on 2008-04-01
does any body read that post???

---

### Post by wolfen69 on 2008-04-01
this has happened to me in the past and a simple reboot fixed it.

---

### Post by prshah on 2008-04-01
> **angel_zone said:**
> i had duall boot ubuntu 7.10 with windows xp and i had 6 drives if that would help

Seeing that you can boot into ubuntu and use your filesystem, I think your problem is an unclean windows shutdown;

Boot into windows, shutdown and restart properly and check if you can see your "drives" (which are not physical, btw) in ubuntu.

---

### Post by nvteighen on 2008-04-01
Go to the terminal and run:
```

mount

```

Please send the output.

That will list which filesystems are mounted (and where).  (What you sent is /etc/fstab, which is a list of what should be mounted at boot... not of what is actually mounted).

(I suspect you're problem is just a GNOME settings issue... There's an option to not show drives on desktop, which I actually use!)

Anyway, are you able to access your data?

---

### Post by angel_zone on 2008-04-01
> **nvteighen said:**
> Go to the terminal and run:
```

mount

```

Please send the output.

That will list which filesystems are mounted (and where).  (What you sent is /etc/fstab, which is a list of what should be mounted at boot... not of what is actually mounted).

(I suspect you're problem is just a GNOME settings issue... There's an option to not show drives on desktop, which I actually use!)

Anyway, are you able to access your data?
sorry for delay i was looking at other forums but i didn't help any way that was the output
noha@Laroza:~$ mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec)
none on /proc type proc (rw,nosuid,nodev,noexec)
udev on /dev type tmpfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/disk/by-uuid/608930e5-41c6-489b-840a-69a5662c3392 on / type ext3 (rw,data=ordered)
/dev/disk/by-uuid/608930e5-41c6-489b-840a-69a5662c3392 on /dev/.static/dev type ext3 (rw,data=ordered)
tmpfs on /var/run type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /var/lock type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw)
tmpfs on /var/run type tmpfs (rw,nosuid,nodev,noexec)
tmpfs on /var/lock type tmpfs (rw,nosuid,nodev,noexec)
noha@Laroza:~$ 
and my proplem is not that my hard drives not visible on the desktop but i can't access them at all under /media

---

### Post by angel_zone on 2008-04-01
> **prshah said:**
> Seeing that you can boot into ubuntu and use your filesystem, I think your problem is an unclean windows shutdown;

Boot into windows, shutdown and restart properly and check if you can see your "drives" (which are not physical, btw) in ubuntu.

i don't think so because i booted into windows and restarted hundreds of time without a result:(

---

### Post by nvteighen on 2008-04-01
Well, then I have no idea on what's going on there, because /etc/fstab does list your disks and so they should be mounted! Sorry...

---

### Post by angel_zone on 2008-04-01
o.k thanx anyway i think this begin to be very serious i'm afraid i'll have to remove ubuntu from my disk and return to windows. i had ubuntu for only a month and i really liked it but i went through tons of proplems in this very short duration i really don't need that thank you anyway

---

### Post by prshah on 2008-04-01
> **angel_zone said:**
> i don't think so because i booted into windows and restarted hundreds of time without a result:(

FIne, why not try ```
sudo mount /dev/sda6
``` or whatever, then post the output of ```
dmesg | tail -15
```

EDIT: Now academic

---

