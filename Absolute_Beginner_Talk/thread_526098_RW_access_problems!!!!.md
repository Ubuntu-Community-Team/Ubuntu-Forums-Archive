---
title: "RW access problems!!!!"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-08-15
:(

Hello.

I have second scsi disk (IBM 10 Gb) installed on my computer and I wanted to use it entayerly. . I formated it with Gparted to ext3 /dev/sdb1.But problem is that I don't have RW access. How to  mount a partition for RW access using the GUI?  (My system is installed on /dev/sda1 and sda2)

Thnx

---

### Post by carloslosgrande on 2007-08-15
[FONT="Courier New"][FONT="Comic Sans MS"]Hi, I'm quite new at this but why don't you try the terminal for this. Enter > man chown and you'll see all the syntax related to the 'chown' command, which can change ownership, ie give you rw.
For my second disk it looks like this [QUOTE]sudo chown <myusername> /media/<devicename>[/QUOTE[/FONT][/FONT]]
[FONT="Comic Sans MS"]I don't know much about a GUI for this.[/FONT]

---

### Post by uzerzero on 2007-08-15
Maybe try forcing it to mount as a R/W drive?

```
mount -tw /dev/sdb1
```

man 8 mount will give you a help menu on all the different uses of mount.

---

### Post by Urko on 2007-08-15
Can you give me more specific commands please becouse I am new in linux?

Thnx

---

