---
title: "A slew of questions"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by CCAT on 2006-11-06
I'm new to Ubuntu and rather new to Linux.  I've used Linux in school for a semester but only at a very very basic level.  I just installed a dual boot system for Windows XP and Ubuntu on my PC today and having some issues setting up.

1.  I have two hard drives.  I managed to mount my second hard drive into my /media directory (/media/storage).  However, I can't seem to write to it.  It's formatted as FAT32 and I've tried in the terminal: "chmod 755 /media/storage" but that hasn't done anything.

2. I've been warned about how I set up permissions and I should change the ownership so it's specific to me.  "chmod /media/storage"?

Any help would be appreciated, thanks.

---

### Post by tribaal on 2006-11-06
1. Are you sure it's FAT32 and not NTFS? No write permission is a common NTFS problem.

2. Hum... I'm not sure I totally understand this question. Are you still referring to your non-writable HDD?

Anyways, a good start for us to figure out how to fix this would be to paste the output of the following command: ```
cat /etc/fstab
```

(Fstab is the file that keeps most of the info about your disks)

Hope I'll be able to help. Otherwise someone else will :) Welcome to Ubuntu!

- trib'

---

### Post by anaconda on 2006-11-06
can you write to your disk if you start nautilus with root rights?
type in terminal:
sudo nautilus
(or gksudo nautilus)

---

### Post by CCAT on 2006-11-06
> **tribaal said:**
> 1. Are you sure it's FAT32 and not NTFS? No write permission is a common NTFS problem.

I'm positive it's not NTFS.

here's the output:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bd069664-bdf4-4746-bfe0-390805a97f29 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=5601dd1b-7cb6-47cd-9e4b-8a2ac2fa6b76 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/sdb1       /media/storage  vfat    defaults        0       0

As for the second question I meant to say that what really happens when you change ownership to a directory?  Does it affect how I access it in any way?

---

### Post by bodhi.zazen on 2006-11-06
```
sudo umount /media/storage
sudo mount <device> /media/storage -t auto -o umask=000
```

Now add this to /etc/fstab> <device> /media/storage auto users,auto,gid=100,uid=1000,umask=000 0 0

You should now be able to muont and umount as a user.

The partition will auto mount at boot.

For more information:

[How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by CCAT on 2006-11-06
> **bodhi.zazen said:**
> ```
sudo umount /media/storage
sudo mount <device> /media/storage -t auto -o umask=000
```

Now add this to /etc/fstab

You should now be able to muont and umount as a user.

The partition will auto mount at boot.

For more information:

[How to fstab](http://ubuntuforums.org/showthread.php?t=283131)


should I remove my last line ni /etc/fstab ?

---

### Post by bodhi.zazen on 2006-11-06
you can modiy it.

```
/dev/sdb1 /media/storage auto users,auto,gid=100,uid=1000,umask=000 0 0
```

After editing fstab umount and re-mount the partition.

---

### Post by bodhi.zazen on 2006-11-06
> **CCAT said:**
> should I remove my last line ni /etc/fstab ?

We are the knights that say "ni"

---

### Post by CCAT on 2006-11-06
> **bodhi.zazen said:**
> you can modiy it.

```
/dev/sdb1 /media/storage auto users,auto,gid=100,uid=1000,umask=000 0 0
```

After editing fstab umount and re-mount the partition.

It worked, fantastic!
I should set my drive to:
```
chown root : /dev/sdb1
```

For security purposes, right?

---

### Post by bodhi.zazen on 2006-11-06
> **CCAT said:**
> It worked, fantastic!
I should set my drive to:
```
chown root : /dev/sdb1
```

For security purposes, right?

/dev/sdb1 should be owned by root. You should change it back if you modified it, otherwise leave it alone.

You set security with the umask=000. If you want only the user to access the drive change to umask=077.

---

