---
title: "Windows wont boot"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by thorwood on 2007-11-26
My friend recently converted to Ubuntu. (Yey!)
But his windows partition won't boot. (lame!)
Seems like F8 wont work after grub,
Help
please :-k

---

### Post by Nano Geek on 2007-11-26
Could you give some more information?
For example, does it give any error messages?

---

### Post by thorwood on 2007-11-26
It just comes up blank

---

### Post by Nano Geek on 2007-11-26
If grub doesn't show that anythings wrong, then it's probably a Windows problem. 
I would suggest either reinstalling Windows, or go to a forum that would have more people who knew more about Windows than most here would.

---

### Post by thorwood on 2007-11-26
thanks for helping

---

### Post by jordanmthomas on 2007-11-26
If you can get the output of 
```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst
``` we can make sure that grub is at least set up right and rule it either a grub problem or a windows problem.

the fdisk command I gave you will **l**ist all the partions on the system and what type they are (ntfs is windows, for example)
the cat command will just output the contents of grub's configuration file so we can see if it matches up with what fdisk shows.

---

