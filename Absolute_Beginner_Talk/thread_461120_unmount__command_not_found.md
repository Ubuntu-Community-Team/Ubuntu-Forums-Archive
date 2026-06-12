---
title: "unmount:  command not found"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-01
Hi,

The mount command works fine, but when I enter:

dace@dace-desktop:~$ sudo unmount /dev/hdb1/store
sudo: unmount: command not found

Does anyone know what I can do to get the unmount command to work?

---

### Post by drowner on 2007-06-01
try umount

---

### Post by TravMan63 on 2007-06-01
Is the syntax umount, not uNmount ?

---

### Post by Outrunner on 2007-06-01
> **TravMan63 said:**
> Is the syntax umount, not uNmount ?

Indeed it is umount

---

### Post by ICUR2Ys on 2007-06-01
I did here is the result.

dace@dace-desktop:~$ unmount /dev/hdb1/store
bash: unmount: command not found

---

### Post by lakersforce on 2007-06-01
It is umount, not unmount!

---

### Post by Lord Illidan on 2007-06-01
The command is not **unmount**. It is [SIZE=3][COLOR=Red]**umount**[/COLOR][/SIZE].

Thus, you should run the command :```
sudo umount /dev/hdb1/store
```

---

### Post by ICUR2Ys on 2007-06-01
Ah, umount is the correct command.  Thank you all.  Everything can be so simple if you understand.  I appreciate the help.

---

### Post by Lord Illidan on 2007-06-01
> **ICUR2Ys said:**
> Ah, umount is the correct command.  Thank you all.  Everything can be so simple if you understand.  I appreciate the help.

No problem..
Why don't you learn some more commands in Linux? It will enhance your experience, and also let you dig deeper into your new OS.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by gentoo_zach on 2007-06-01
If you want a nice, compact resource on Linux commands (primarily for BASh), this book is pretty good:

[http://www.amazon.com/Linux-Phrasebook-Developers-Library-Granneman/dp/0672328380/ref=pd_bbs_sr_1/002-1887138-4808059?ie=UTF8&s=books&qid=1180713342&sr=8-1](http://www.amazon.com/Linux-Phrasebook-Developers-Library-Granneman/dp/0672328380/ref=pd_bbs_sr_1/002-1887138-4808059?ie=UTF8&s=books&qid=1180713342&sr=8-1)

Hope that helps.

---

### Post by ICUR2Ys on 2007-06-01
> **Lord Illidan said:**
> No problem..
Why don't you learn some more commands in Linux? It will enhance your experience, and also let you dig deeper into your new OS.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

I bought A Practical Guide To Linux ... Highly recommended, I tried to look up mount.  It is not in the command list.  I intend to learn most of the commands that I will normally need and look up the rest.  

But when my reference doesn't have this command set I turned to you folks for help.  After doing a search for unmount of course.

---

### Post by lakersforce on 2007-06-01
I still recommend reading [this guide.]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html")

---

