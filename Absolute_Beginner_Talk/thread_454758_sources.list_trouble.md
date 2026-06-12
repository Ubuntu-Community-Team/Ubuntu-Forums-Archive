---
title: "sources.list trouble"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by JordanII on 2007-05-25
I am having trouble adding a line at the end of etc/apt/sources.list. How should I do this? Thanks!

~Jordan

---

### Post by starcraft.man on 2007-05-25
> **JordanII said:**
> I am having trouble adding a line at the end of etc/apt/sources.list. How should I do this? Thanks!

~Jordan

Just open it up with:

```
gksudo gedit /etc/apt/sources.list
```
in the terminal of course (Applications > Accessories > Terminal)

then copy and paste the line from a web page and put it right at the end. Make sure you don't put a # in front or it will not be read at update.

Easy enough, now to reboot into windows... bye bye, got to print something out in publisher.

---

### Post by BHelts on 2007-05-25
```
gksudo gedit /etc/apt/sources.list
```
will open up sources.list
add your line at the bottom and click on the save icon.  that should do it.
you may choose to back up your sources.list first.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```
i think that is the right command.

---

### Post by JordanII on 2007-05-25
Thanks! It worked.

~Jordan

---

