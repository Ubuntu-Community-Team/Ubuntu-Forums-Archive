---
title: "How to mount my hard disk?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by nafiziut on 2007-07-15
Hello,
I am new in ubuntu. After installing it  I found that it is not showing one of my hard disk partition on the desktop.I have primary and slave hard disk.The  partition is in the slave one.

What to do?

---

### Post by vanadium on 2007-07-15
Should have been detected and configured during installation. Does the partition show up in the output of the command

sudo fdisk -l

Additionally, post also the output of 

mount

---

### Post by shoaibi on 2007-07-15
after running 

sudo fdisk -l

this would be of great help to you:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows)

---

### Post by regomodo on 2007-07-15
press alt+f2 and type in the word "terminal"

a new box will pop up.

copy the following

```
sudo fdisk -l

```

and paste it into this new box (terminal)

press your "enter" key and type in **your** password.

Now, copy what you get in the terminal and paste it here in this thread

---

