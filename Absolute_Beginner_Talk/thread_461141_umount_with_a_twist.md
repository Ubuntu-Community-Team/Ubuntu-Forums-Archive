---
title: "umount with a twist"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-01
I now have the right command but I still don't know what I am doing.  Here is the Problem:

dace@dace-desktop:~$ sudo umount /store
umount: /store: not mounted
dace@dace-desktop:~$ sudo mount /store
mount: can't find /store in /etc/fstab or /etc/mtab
dace@dace-desktop:~$ sudo mount /dev/hdb1/store
mount: can't find /dev/hdb1/store in /etc/fstab or /etc/mtab
dace@dace-desktop:~$ cd /store
dace@dace-desktop:/store$ sudo umount /store
umount: /store: not mounted
dace@dace-desktop:/store$ sudo mount /store
mount: can't find /store in /etc/fstab or /etc/mtab
dace@dace-desktop:/store$ 

Sorry about my ignorance here but I just don't know how to make this work.

---

### Post by Cypher on 2007-06-01
Ok..first 
```

mount

``` 
this will list all the partitions that are mounted, if "store" isn't listed, it isn't mounted.

Assuming that "/dev/hdb1" is the partition you want mounted on "store", you use
```

sudo mount /dev/hdb1 /store

```
Notice the space between "/dev/hdb1" and "/store". This assumes that the partition is something Linux can figure out and to use default options. In most cases, this will work fine.

If you wish to have this particular partition mounted every time you boot your machine, you'd want to add an entry to the /etc/fstab file. But let's first get this mounted before we get to that..

---

### Post by ICUR2Ys on 2007-06-01
OK cypher I tried without success;

dace@dace-desktop:~$ sudo mount /dev/hdb1 /store
dace@dace-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda2 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /store type ext3 (rw)     <<<  it shows here
dace@dace-desktop:~$

So it is mounted now to unmount it.

dace@dace-desktop:~$ sudo umount /dev/hdb1 /store
umount: /dev/hdb1: not mounted
umount: /dev/hdb1: not mounted
dace@dace-desktop:~$ sudo umount /dev/hdb1/store
umount: /dev/hdb1/store: Not a directory
dace@dace-desktop:~$ 

dace@dace-desktop:~$ sudo umount /dev/hdb1/store
umount: /dev/hdb1/store: Not a directory
dace@dace-desktop:~$ sudo umount /store
umount: /store: not mounted
dace@dace-desktop:~$

When I run mount now in fact it is not mounted.

I appreciate your help.  I can make this work now but it is still confusing responses.  But it does work.  Thank you.

---

### Post by Outrunner on 2007-06-01
Doesn't just 

```
sudo umount /dev/hdb1
```

work??

---

### Post by Cypher on 2007-06-01
OK..a simple primer.:)

To mount
```

sudo mount <partition or file> <destination>

```

After this, the partition or file you mounted should be visible in the <destination> directory. So you can "cd" over to it, "ls" the files and do other things.

To unmount
```

sudo umount <destination>

```

This will unmount the <destination> you need not specify WHAT you used to mount this particular directory.

---

### Post by Cypher on 2007-06-01
> **Outrunner said:**
> Doesn't just 

```
sudo umount /dev/hdb1
```

work??

Umm no..you do not unmount the device, but rather the directory on which this device is mounted on..

---

### Post by Outrunner on 2007-06-01
Actually, I just tried unmounting my external HD with

```
sudo umount /dev/sdb1
``` and it worked. So, I guess you can unmount the device

---

### Post by Cypher on 2007-06-01
Actaully you're correct..umount can take either the device or dir. It's just that I've always used the directory and never the device..and to think I've only been using Linux for about 10 years..:)

---

### Post by Outrunner on 2007-06-01
You know, it's the opposite for me, I always used umount on the device. But I've just tried on the destination directory and that works too. Neat!

---

