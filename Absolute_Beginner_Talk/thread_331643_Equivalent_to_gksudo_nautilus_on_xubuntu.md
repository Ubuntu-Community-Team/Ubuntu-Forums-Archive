---
title: "Equivalent to gksudo nautilus on xubuntu?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-01-04
Excuse me, but what was the equivalent of gksudo nautilus in xubuntu?

---

### Post by taurus on 2007-01-04
You mean "gksudo thunar"!

---

### Post by Jorge32 on 2007-01-04
perfect, thanks!

---

### Post by kebes on 2007-01-04
Well (in KDE, but probably the same in other desktop environments) I've never had a problem just opening a terminal and going "sudo konqueror" (or whatever program). Then it opens up with root privileges, and keeps running as long as you don't close the terminal!

Any reason this wouldn't work?

---

### Post by Bachstelze on 2007-01-04
In KDE, you must use kdesu instead of sudo to rn graphical apps as root. Using sudo can mess up your file permissions realy badly.

---

### Post by dermotti on 2007-01-06
> **kebes said:**
> Well (in KDE, but probably the same in other desktop environments) I've never had a problem just opening a terminal and going "sudo konqueror" (or whatever program). Then it opens up with root privileges, and keeps running as long as you don't close the terminal!

Any reason this wouldn't work?

gksudo does basically the same thing as sudo, except for you dont need to leave the terminal window open.

I have a "gksudo thunar" in my start menu just incase i need a root window., and i dont have that annoying terminal popping up :-)

---

