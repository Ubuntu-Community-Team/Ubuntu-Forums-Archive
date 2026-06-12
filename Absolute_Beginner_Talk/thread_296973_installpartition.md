---
title: "install/partition"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by f250ld on 2006-11-10
I'm trying to manually create partitions to install ubuntu 6.10, I have three partitions, one is \dev\hda1, the 2 new ones are new partition 1 and 2, how do i make one of these a root to install.

---

### Post by happy-and-lost on 2006-11-10
It should give you the option of making hda2/3 "/" at install.

---

### Post by taurus on 2006-11-10
If you have three partitions, then the first one is /dev/hda1, the second one is /dev/hda2, and the third one is /dev/hda3!!!

---

### Post by f250ld on 2006-11-10
I just tried making the partions and got an error saying "check file system on dev/hda1 for errors (and if possible) fix them.

---

### Post by taurus on 2006-11-10
How did you partition your harddrive anyway?

---

### Post by f250ld on 2006-11-10
I was using the manual option through the install

---

### Post by taurus on 2006-11-10
What is the output of this command, from the LiveCD, then?

```
sudo fdisk -l
```

---

