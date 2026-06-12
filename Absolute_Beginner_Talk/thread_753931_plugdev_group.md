---
title: "plugdev group"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by luckymancvp on 2008-04-13
The owner-group of almost file in my computer is plugdev.
So I can't change my file, edit,....
How to do it.Please help me.

---

### Post by luckymancvp on 2008-04-13
Please help me. I can't do anything with my file.

---

### Post by nick_h on 2008-04-13
All files under you home directory should be owned by you and in a group with the same name as your username.  You should be able to create, delete and edit files under your home directory by default.  This is normally where user files should be stored.

The plugdev group is normally assigned to filesystems contained on removable media.  I think by default you should be a member of this group.  If not you should add yourself to the plugdev group.

---

### Post by PJSingh5000 on 2008-04-30
(1) Add yourself to the plugdev group...
```
$ sudo usermod -a -G plugdev <your user id>
```

(2) Change the ownership of your own files to your group...
```
chown -R <your user id>:<your user id> /home/<your user id>
```

Note that many of the files on your system should be owned by root, except those in your home directory.  Something must have gone wrong with your installation.

---

