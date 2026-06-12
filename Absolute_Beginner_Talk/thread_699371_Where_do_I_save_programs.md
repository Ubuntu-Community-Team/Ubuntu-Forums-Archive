---
title: "Where do I save programs?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jimcameron on 2008-02-17
Hi folks,

I'm new to Linux (and i'm loving it!) just a quick question. I downloaded real player to listen to live radio etc, and at the moment it's siting on my desktop. Is there a place where i should put programs? 

For example is there the equivalent of C: Drive in Windows?

Hope this makes sense,

Cheers Jim

---

### Post by wolfen69 on 2008-02-17
see this [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)
also look at installing programs in ubuntu [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jan quark on 2008-02-17
no the file management is different in linux read this fo more info
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)


when you download real player installer from here
[https://player.helixcommunity.org/2004/downloads/](https://player.helixcommunity.org/2004/downloads/)

you have to run
```

chmod 755 realplay-10.0.4.750-linux-2.2-libc6-gcc32-i586.bin
```
```
sudo ./realplay-10.0.4.750-linux-2.2-libc6-gcc32-i586.bin
```

and follow the instructions. When asked where to install:


```
 /usr/bin
```

---

### Post by lncoll on 2008-02-17
Hi:

Disk organization is different in Unix/Linux, here you have a tree structure that begins in / the root directory.
The root is a partition of one of your hard disks, from here you have directories.
If you have another partition or disk in use ( say mounted ) it is mounted in a folder. to see how is in your system type at a console 

```
user@host:~$mount

/dev/sda4 on / type reiserfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda2 on /boot type ext3 (rw)
/dev/sdb1 on /dos type vfat (rw,utf8,umask=007,gid=46)
/dev/sda3 on /home type reiserfs (rw)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

This shows how are disks used in your system.

Here there are fisical and virtual units mounted in the filesistem, the ones starting with /dev/ are fisical ones, try this on your system to see what do you have.

From here I reccomend you looking for a tutorial, a good one is "The official Ubuntu book" and many others in the net.

---

