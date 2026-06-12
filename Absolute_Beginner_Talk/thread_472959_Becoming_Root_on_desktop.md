---
title: "Becoming Root on desktop"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by JJFO on 2007-06-13
I want to unmount a drive, and if I right click the drive icon on my desktop there is an unmount drive option, but I have to be root to do that, and I have no idea how to become root outside a folder or the terminal. Can anyone help?

---

### Post by Nekiruhs on 2007-06-13
```
gksudo nautilus
```
Then just browse to /home/YOURUSERNAME/Desktop

---

### Post by starcraft.man on 2007-06-13
Nekiruhs' solution will work. I don't think that opening nautilus with sudo powers every time you need to do something like this is a good idea though.
[URL="http://www.linuxcommand.org/lts0070.php"]
This tut will teach you about permissions,[/URL] after you read through it you will know how to reassign yourself permission to control the drive/all folders inside. Then you can do it without sudo.

It's advisable you understand this, because the permission structure is very pervasive in Linux, its a core feature and you don't want to run Sudo Nautilus every time you need to do something.

---

