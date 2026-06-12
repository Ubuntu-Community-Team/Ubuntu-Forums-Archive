---
title: "Missing xp on grub"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-05-21
For some reason Windows XP has disappeared as a second boot option when I boot up. Are there any ways that I can get it back?

---

### Post by oilchangeguy on 2007-05-21
things like this just don't happen by themselves. what changes have you made recently.

---

### Post by Benbow on 2007-05-21
The only thing I can think of is the update to feisty??

---

### Post by Cypher on 2007-05-21
That is definitely one possibility. When I upgraded from Edgy to Feisty, I didn't lose my XP boot option. What does your /boot/grub/menu.lst look like?

---

### Post by Benbow on 2007-05-21
It has the usual Ubuntu option and then the only other option is "windows NT/2000/XP loader" which sends the system into reinstallation of xp mode!!
The original xp partition is still there and it looks complete.

---

### Post by steve.horsley on 2007-05-21
Here is a typical stanza for windows:
> title          Microsoft Windows XP Professional
root           (hd0,0)
savedefault
makeactive
chainloader    +1


It is intended for windows on hda1. (Grub numbers start at 0) You will need to figure out the right drive number yourself. Add these lines to /boot/grub/menu.lst either before or after the section marked as the automagic installer section.

HTH

P.S.
You can edit htat file with the command:
**gksudo gedit /boot/grub/menu.lst**

---

