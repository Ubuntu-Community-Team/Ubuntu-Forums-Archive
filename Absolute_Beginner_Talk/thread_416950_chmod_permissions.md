---
title: "chmod permissions"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by thomas.hoyland on 2007-04-21
hi all
i moved loads of folders with loads of files from an ntfs drive to my xfs usb hdd

however the new folders and all included files i need to grant write/read/execute permission to

how do i do it ?

sorry, its prob a stupid question

---

### Post by heimo on 2007-04-21
Perhaps these will help you?
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)

---

### Post by codingmaster on 2007-04-21
Hi!

This gives world rwx permissions:

chmod -R ugo+rwx FOLDERNAME

-R <- recursive
u = user
g = group
o = owner
+ = add
rwx = read write execute

Regards, Georgy Berdyshev

---

### Post by thomas.hoyland on 2007-04-21
> **codingmaster said:**
> Hi!

This gives world rwx permissions:

chmod -R ugo+rwx FOLDERNAME

-R <- recursive
u = user
g = group
o = owner
+ = add
rwx = read write execute

Regards, Georgy Berdyshev

outstanding my friend!
many thanks, once again the ubuntu forum shows how great it and its member are!:popcorn:

---

### Post by codingmaster on 2007-04-21
Hello!

> **thomas.hoyland said:**
> outstanding my friend!
many thanks, once again the ubuntu forum shows how great it and its member are!:popcorn:

Thanks a lot!

Regards, Georgy Berdyshev

---

