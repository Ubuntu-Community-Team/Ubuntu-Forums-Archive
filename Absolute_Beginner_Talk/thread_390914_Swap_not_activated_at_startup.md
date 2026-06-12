---
title: "Swap not activated at startup"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Lexyboy on 2007-03-22
Hi all,

I've recently noticed that my swap isn't mounted at startup (since upgrading to edgy I guess).  I ran gparted, which showed what was my swap (/dev/sda4) was 'filesystem not recognised'.  I reformatted as swap, and did 'swapon' from gparted.  All well, swap working fine.  However, it's not started on restarting the system, and additionally entering 
```
sudo swapon -a
```
gives:
```
swapon: cannot stat /dev/disk/by-uuid/7a85dc79-c6a1-4f51-a491-e8f62cd500d5: No such file or directory
```

So, I'm guessing that when I reformatted the UUID of the partition changed, which is why gparted can mount it but the swapon command doesn't.  (Probably miles out as I'm a noob).

Any ideas on how to get it working normally again?

My fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=79752e89-36c5-4b5e-83c6-ab6095a7a740 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=A82A-F795 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=60B08807B087E240 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda4 -- converted during upgrade to edgy
UUID=7a85dc79-c6a1-4f51-a491-e8f62cd500d5 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2007-03-22
Edit /etc/fstab from a terminal with

```
kdesu kate /etc/fstab
```
and replace this line

```
UUID=7a85dc79-c6a1-4f51-a491-e8f62cd500d5 none swap sw 0 0
```
with this one.

```
/dev/sda4   none   swap   sw   0   0
```
Save it and reboot.

Now, see if your swap is mounted.

```
free
```

---

### Post by igknighted on 2007-03-22
Use sda4 for taurus' suggestion, sda2 is your vfat (fat32) partition.

---

### Post by Lexyboy on 2007-03-22
Thanks guys, worked a treat!  Just wondering, why does edgy relpace the easy to understand /dev/sdaX with a UUID?  A simple path seems much easier to understand - I didn't want to fiddle about too much as I assumed they were there for a reason.

Thanks anyway, now will have to see if it gets used (I only noticed there was no swap by chance, looking in sysinfo)

---

### Post by mcduck on 2007-03-22
> **Lexyboy said:**
> Thanks guys, worked a treat!  Just wondering, why does edgy relpace the easy to understand /dev/sdaX with a UUID?  A simple path seems much easier to understand - I didn't want to fiddle about too much as I assumed they were there for a reason.

Thanks anyway, now will have to see if it gets used (I only noticed there was no swap by chance, looking in sysinfo)

The old /dev/xxxx style has the problem that if you change the hard drive to another connector it changes, while UUID stays same. Also you can't use the /dev/xxxx style for removable drives as their device also changes depending on which order they are recognized, but once again using UUID allows you to configure removable drives in fstab.

---

### Post by louieb on 2007-03-22
If you want to find  the uuid: 
```
ls -l /dev/disk/by-uuid/
```

---

### Post by ukripper on 2007-06-08
> **louieb said:**
> If you want to find  the uuid: 
```
ls -l /dev/disk/by-uuid/
```

I was just looking for UUID thanks.

---

