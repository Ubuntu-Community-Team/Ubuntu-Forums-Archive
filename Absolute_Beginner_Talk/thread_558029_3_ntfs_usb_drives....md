---
title: "3 ntfs usb drives..."
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by hacklab on 2007-09-23
If I do: ls -la /media/

root@linux:~# ls -la /media
total 68
drwxr-xr-x  7 root root  4096 2007-09-23 19:15 .
drwxr-xr-x 21 root root  4096 2007-09-23 18:40 ..
lrwxrwxrwx  1 root root     6 2007-09-23 18:28 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-09-23 18:28 cdrom0
lrwxrwxrwx  1 root root     7 2007-09-23 18:28 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-09-23 18:28 floppy0
-rw-r--r--  1 root root     0 2007-09-23 19:15 .hal-mtab
--wxr-x---  1 root root     0 2007-04-15 13:56 .hal-mtab-lock
drwxr-xr-x  2 roko roko  4096 2007-09-23 18:56 sdb1
drwxr-xr-x  2 roko roko  4096 2007-09-23 18:56 sdc1
dr-xr-xr-x  1 root root 45056 2007-09-23 19:04 sdd1

sdb1, sdc1, sdd1 are usb drives.
When Im in file maneger i can see all 3 drives, but 2 of them say an error when I click on them:

**You are not privileged to mount the volume '320GB'**

What do i do so all 3 drives are read/write ?

---

### Post by Pumalite on 2007-09-23
Sudo chmod 777 /dev/xxx

---

### Post by Pumalite on 2007-09-23
Do you have ntfs-3g installed?

---

### Post by hacklab on 2007-09-23
didnt work:

root@linux:~# sudo chmod 777 /dev/xxx
chmod: cannot access `/dev/xxx': No such file or directory

---

### Post by hacklab on 2007-09-23
no i dont have ntfs-3g installed

---

### Post by mlentink on 2007-09-23
> **hacklab said:**
> no i dont have ntfs-3g installed
```

sudo apt-get install ntfs-3g
```

And, ah, replace 'xxx' with the mountname of the drive in question, since you most likely will not have a drive mounted as 'xxx'

---

### Post by logos34 on 2007-09-23
what does 
[B]
mount [/B]

show?

---

