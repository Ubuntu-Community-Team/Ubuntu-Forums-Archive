---
title: "can't read or write on ntfs after installing kdedu and edubuntu packages"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by princeza on 2008-01-12
I have Ubuntu 7.10 and ntfs3g installed. after installing the packages, I can't read or write from hda1 and hda5 anymore. the links to them are also removed from the desktop and Places.

after typing sudo fdisc -l I get the following:
```
/dev/hda1   *           1        2079    16699536    7  HPFS/NTFS
/dev/hda2            2080        9220    57360082+   f  W95 Ext'd (LBA)
/dev/hda3            9221        9729     4088542+  83  Linux
/dev/hda5            2080        5903    30716248+   7  HPFS/NTFS
/dev/hda6            5904        6414     4104576   83  Linux
/dev/hda7            6415        6676     2104483+  82  Linux swap / Solaris
/dev/hda8            6677        9220    20434648+  83  Linux
```

and with mount:
```
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda6 on /home type ext3 (rw)
/dev/hda8 on /usr type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

can someone help?

---

### Post by taurus on 2008-01-12
Try

```
sudo mkdir /media/hda1 /media/hda5
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
sudo mount -t ntfs-3g /dev/hda5 /media/hda5
df -h
```
And if you get a warning message about that your ntfs partitions didn't unmount cleanly, you can use the force option to mount them.

```
sudo mount -t ntfs-3g /dev/hda1 /media/hda1 -o force
sudo mount -t ntfs-3g /dev/hda5 /media/hda5 -o force
df -h
```

---

### Post by princeza on 2008-01-13
When I typed in the mount command like you said, the system printed out two options:
1. something about Windows device drivers, that it didn't shut down properly,
2. that I could force the mount anyway.

So I booted Windows and shut down properly. Now I can see hda1 and hda5 normally again.

Thank you for your answer!

---

