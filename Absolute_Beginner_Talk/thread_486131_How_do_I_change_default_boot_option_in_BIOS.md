---
title: "How do I change default boot option in BIOS??"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by kidob on 2007-06-27
I've noticed that when I'm running kernel 16 my wireless is stop and go and the system frequently crashes, usually at the same time the wireless starts acting up. This is no major issue because when I run kernel 15 the wireless runs flawlessly and it never crashes. It's just a pain to always have to watch the screen while booting so I can select kernel 15 instead of 16, which is at the top of the list (poor XP is way down at the bottom :popcorn:).

I can't figure out how to make kernel 15 the automatic first choice so I can do other things while waiting for my computer to power up. Is this possible? Thanks :D

---

### Post by PCFascist on 2007-06-27
Change it from inside Ubuntu, edit the file /boot/grub/menu.lst. There will be a line that says
```

default 0
```

Simply change '0' to the number of your  install. For example, if your grub has three entries and u15 is the third, change default to 2 (0 is the first entry, not 1).

[http://www.linuxquestions.org/questions//showthread.php?t=456724](http://www.linuxquestions.org/questions//showthread.php?t=456724)

---

### Post by kidob on 2007-06-27
> **PCFascist said:**
> Change it from inside Ubuntu, edit the file /boot/grub/menu.lst. There will be a line that says
```

default 0
```

Simply change '0' to the number of your  install. For example, if your grub has three entries and u15 is the third, change default to 2 (0 is the first entry, not 1).

[http://www.linuxquestions.org/questions//showthread.php?t=456724](http://www.linuxquestions.org/questions//showthread.php?t=456724)

Thanks I found the menu file but when I open it it opens as read only and I can figure out how to edit it. I don't understand this because it's my own personal computer so I usually have no problem making system changes, it just asks for my password; but in this case when I change the default in the file it won't let me save. How can I get around this?

---

### Post by southernman on 2007-06-27
from a terminal do:

> gksudo gedit /boot/grub/menu.lst

It may be your computer, but this file is owned by root. It's for your protection believe it or not. :p

---

