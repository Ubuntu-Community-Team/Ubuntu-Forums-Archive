---
title: "cannot access second hard drive"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by kenandjo on 2007-11-03
Hi,
The second hard drive on my computer keeps preventing me from accessing it.  I believe I can mount it.  I can then see the single folder it contains : "lost+found".  It is here I get the following error message:
[COLOR="Red"]You do not have the permissions necessary to view the contents of "lost+found"[/COLOR].

Can anyone help me?
I run Gutsy...

---

### Post by chggr on 2007-11-03
The folder "lost+found" is readable only by root.
It contains lost files that have been found after a disk checkup. On most cases, it simply contains nothing.

Use a console and issue the command:
sudo bash

This will give you a root shell. Then you can use the cd command to see what is inside the folder "lost & found". If you see nothing, then it is safe to delete it.

---

### Post by kenandjo on 2007-11-03
thanks for that.  I have the root shell ok, but what is and how do you action the "cd command"?

---

### Post by Partyboi2 on 2007-11-03
```
sudo bash
```Then change directory (cd) to the folder
```
cd /lost+found
```then list the contents
```
ls
```:)

---

