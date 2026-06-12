---
title: "[SOLVED] Access Vista after installing ubuntu"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Hobbs131 on 2007-10-23
How come after I got Vista and Ubuntu dual booted I can not access my vista files on my ubuntu?
I can get on both seperately but I am not able to access my vista files when on ubuntu.

---

### Post by jualin on 2007-10-23
If you have the Ubuntu 7.10 you should not have this problem. If you have another version of ubuntu just go to the package manager and download Ntfs-3g package. This package lets you read and write your NTFS (Windows) partition from Ubuntu. After you install this package, try to access to the windows partition, usually called SDA1 or Sda2. I hope this helps:)

---

### Post by Hobbs131 on 2007-10-23
I do have ubuntu 7.10 lol so yea thats why im confused

---

### Post by rudeboyskunk on 2007-10-23
I always just typed this command when I used Windows:

```
sudo mount /dev/*whatever* /mnt
```

---

### Post by Hobbs131 on 2007-10-23
ok...ill try that when i have a little more time...if anyone else has suggestions also please post

---

### Post by jualin on 2007-10-23
maybe you did not reboot the Windows partition correctly. Sometimes you have to log into windows and then shutdown the computer correctly and then starting Ubuntu. It has happened to me before, and after a clean reboot everything went back to normal.

---

### Post by Hobbs131 on 2007-10-23
thanks jualin...after i logged off correctly on vista it worked.

---

### Post by jualin on 2007-10-23
Good to hear that it worked

---

