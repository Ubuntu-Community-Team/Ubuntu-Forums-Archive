---
title: "Cant mount drive"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Muntted on 2008-02-29
I am trying to make a softraid 5.
I processed the raid... it set up correctly. When I go to format it I get:
> Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

Then when I go to mount it:
> mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


any ideas guys?

---

### Post by dstew on 2008-02-29
> Attempt to read block from filesystem resulted in short read while creating root dirThis suggests that the filesystem has some errors on it. You can run ```
sudo [fsck]("http://linux.die.net/man/8/fsck") -a
``` on that device to see.

---

### Post by Muntted on 2008-02-29
> **dstew said:**
> This suggests that the filesystem has some errors on it. You can run ```
sudo [fsck]("http://linux.die.net/man/8/fsck") -a
``` on that device to see.

It shouldnt be, I have created the array twice and tried formatting it multiple times.
in anycase that fsck code only gives me:
> ubuntu@ubuntu:~$ sudo fsck -a
fsck 1.40.2 (12-Jul-2007)


---

### Post by dstew on 2008-02-29
You have to add the device name to the command:```
sudo fsck -a /dev/sda1
```or whatever the name is.

---

