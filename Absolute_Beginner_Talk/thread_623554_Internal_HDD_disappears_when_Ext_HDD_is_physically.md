---
title: "Internal HDD disappears when Ext HDD is physically disconnected"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by martinja on 2007-11-26
I have just found something quiet inexplicable. When I disconnect my External Harddrive (only has 1 partition) then any reference to the secondary internal harddrive disappears. The following is without external harddrive physically connected:

    martinjp@martinjp-server:~$ mount -l
    /dev/sda1 on / type ext3 (rw,errors=remount-ro) []
    proc on /proc type proc (rw,noexec,nosuid,nodev)
    /sys on /sys type sysfs (rw,noexec,nosuid,nodev)
    varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
    varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
    udev on /dev type tmpfs (rw,mode=0755)
    devshm on /dev/shm type tmpfs (rw)
    devpts on /dev/pts type devpts (rw,gid=5,mode=620)
    lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
    securityfs on /sys/kernel/security type securityfs (rw)

This is the same query with external harddrive connected:

    martinjp@martinjp-server:~$ mount -l
    /dev/sda1 on / type ext3 (rw,errors=remount-ro) []
    proc on /proc type proc (rw,noexec,nosuid,nodev)
    /sys on /sys type sysfs (rw,noexec,nosuid,nodev)
    varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
    varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
    udev on /dev type tmpfs (rw,mode=0755)
    devshm on /dev/shm type tmpfs (rw)
    devpts on /dev/pts type devpts (rw,gid=5,mode=620)
    lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
    securityfs on /sys/kernel/security type securityfs (rw)
    /dev/sdb5 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma sk=077,usefree) [LOCAL DISK]
    /dev/sdb1 on /media/EXT DRIVE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma sk=077,usefree) [EXT DRIVE]

Why should the fact that the external harddrive is connected or not means that the internal harddrive is detected???
How can I make sure that the internal harddrive stays connected (mounted??) so can put my /home directory on it?
Thanks for your consideration.

---

