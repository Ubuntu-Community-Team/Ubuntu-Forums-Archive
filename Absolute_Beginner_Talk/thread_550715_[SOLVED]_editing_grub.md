---
title: "[SOLVED] editing grub?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-09-14
I must say the grub loader in linux looks much friendlier than the windows multi os loader.
My grub shows 4 enties for ubuntu (2 different versions + recovery modes for both)
is this normal.

Also I would like to know how do I change the default boot item and the timeout

---

### Post by Golyadkin on 2007-09-14
Yup, this is normal. It shows the last few kernel versions automatically incase you have to fallback when something goes wrong. 
I think the config file you want is /etc/grub/menu.lst

---

### Post by overdrank on 2007-09-14
> **bigmonmulgrew said:**
> I must say the grub loader in linux looks much friendlier than the windows multi os loader.
My grub shows 4 enties for ubuntu (2 different versions + recovery modes for both)
is this normal.

Also I would like to know how do I change the default boot item and the timeout

Hi and welcome,  yes it is normal after a kernel update, and this link is good for the grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by nick_h on 2007-09-14
The config file is /boot/grub/menu.lst - edit it with,
```
gksudo gedit /boot/grub/menu.lst
```
or an editor of your choice.

The options default and timeout are the first two in the file.  The comments explain how to edit them.

---

### Post by bigmonmulgrew on 2007-09-14
cheers thanks a lot guys

---

