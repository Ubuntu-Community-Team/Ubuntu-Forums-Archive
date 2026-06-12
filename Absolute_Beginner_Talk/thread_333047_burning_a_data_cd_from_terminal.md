---
title: "burning a data cd from terminal"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-06
I'm trying to burn a data cd from the terminal, and was told to use a form like:

cdrecord dev=/dev/hdc speed=24 driveropts=burnfree -dao -data /path/to/files 

my device name, however is incorrect.  How would I be able to find the correct one for my system?

---

### Post by taurus on 2007-01-06
Probably need to look in your /etc/fstab!!!

```
cat /etc/fstab
```

---

### Post by IYY on 2007-01-07
I don't think the device name is incorrect. /dev/hdc is where the cdrom is usually located. Even /dev/cdrom is usually linked to it:

```
ilya@muddy:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2007-01-06 13:21 /dev/cdrom -> hdc
```

---

### Post by taurus on 2007-01-07
Actually, some people have their CD-ROM as /dev/hdd.

---

