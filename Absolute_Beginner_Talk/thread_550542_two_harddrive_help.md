---
title: "two harddrive help"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by PoorGuy707 on 2007-09-14
im running Ubuntu,
and im a noob

but a friend of mine wants to join the Ubuntu club,
he has two hdds,
he wants one for windows and the other for ubuntu,
but Ubuntu isnt noticing the second hdd that he wants Ubuntu on,

any suggestions on what to do??

---

### Post by bodhi.zazen on 2007-09-14
Can you post the output of :

```
sudo fdisk -l
```

If that command does not list 2 hd, we need more details. What kind of HD, and is it working in other OS ? ie is it a hard ware problem.

Also, have you formatted the disk ? is it new or old ? if old, what was on it ? what file system ? FAT, NTFS ?

---

### Post by PoorGuy707 on 2007-09-14
it sees the hard drive it just cant create a partition on it 
he can acces the hard drive files with the live disc too
it shows an error message after it starts to install saying it cant create the partition thats all

---

### Post by Maestro23 on 2007-09-14
> **PoorGuy707 said:**
> it sees the hard drive it just cant create a partition on it 
he can acces the hard drive files with the live disc too
it shows an error message after it starts to install saying it cant create the partition thats all

Is that all that's in the error msg?

The drive is unmounted when you are trying to partition it right?

---

