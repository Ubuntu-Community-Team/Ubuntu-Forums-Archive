---
title: "[SOLVED] Windows Partition: Gone"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by saxonjf on 2007-11-06
I have used my windows partition to keep a bunch of files, and keep my smaller Linux partition clean.

But for reasons I cannot understand, my windows partition has disappeared from my Linux desktop.

I can get to /media/hda1, but it is empty, when before, it would get me to my windows.

I looked up /dev/hd1, per gparted, but it wouldn't open up at all.  GParted shows it there, but I can't get it to open

Can I get some help here?

---

### Post by macdo on 2007-11-06
Please post the output of mount in a console : 

```
mount
```

---

### Post by JBAlaska on 2007-11-06
Check this [Page](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by saxonjf on 2007-11-06
```
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

GParted said that the status of /dev/hda1 was unmounted

---

### Post by saxonjf on 2007-11-06
I got into the terminal, and did
```
sudo mount -a
```

then it told me I had to enter in a force line, which I did, but then it said I wasn't the root, so I added sudo to it, and I have remounted the partition.

Thanks for the help.

---

