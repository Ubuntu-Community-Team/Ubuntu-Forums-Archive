---
title: "I lost my windows mount with upgrade."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Deguello on 2007-04-24
I upgraded to Feisty. My prior install had a good windows partition mount, but I cannot get it to mount now. I tried to use NTFS Partition to mount it, but it will not. Here is a list of my mounts.....is there omething else I can do?


deguello@XXXXXXXX.~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/MP30207 type iso9660 (ro,noexec,nosuid,nodev,noatime,uid=1000,utf8)


Thanks!

---

### Post by Jazztux on 2007-04-25
Hi,
I upgraded my Ubuntu too, but all my windows partitions are accessible as always. Do you know what's the windows partition you have to mount?

---

