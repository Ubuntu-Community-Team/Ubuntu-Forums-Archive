---
title: "Linux or Linux-based?"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by j.hill on 2005-08-29
I'm wondering about the wording of the ubuntulinux.org home page, which describes Ub. as "a complete Linux-based operating system".  This makes it sound like Mac OS X -- not Unix, but Unix-based.  Is it Linux or isn't it?  If it's not, then what are the differences between this and "real" Linux?

---

### Post by grim42 on 2005-08-29
Technically speaking, Linux is just the operating system kernel. So what this is saying is that Ubuntu is an operating system based on (ie. using) the Linux kernel.

Ubuntu is a GNU/Linux distribution just like Debian, Fedora, Mandriva, Slackware... etc.

---

### Post by poofyhairguy on 2005-08-29
[QUOTE=j.hill]I'm wondering about the wording of the ubuntulinux.org home page, which describes Ub. as "a complete Linux-based operating system".  This makes it sound like Mac OS X -- not Unix, but Unix-based.  Is it Linux or isn't it?  If it's not, then what are the differences between this and "real" Linux?[/QUOTE]

Linux is not Unix. It is a copy of a Unix, Minix.

Linux is a kernel. IT itself is not a whole OS:

[http://en.wikipedia.org/wiki/Kernel_%28computer_science%29](http://en.wikipedia.org/wiki/Kernel_%28computer_science%29)

Ubuntu is a desktop OS. It uses Linux as its kernel. It is a "real" Linux OS. It uses other tools in the Gnu system, that system includes Linux:

[http://en.wikipedia.org/wiki/GNU](http://en.wikipedia.org/wiki/GNU)

[http://en.wikipedia.org/wiki/Ubuntu_Linux](http://en.wikipedia.org/wiki/Ubuntu_Linux)

Read this last:

[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

---

### Post by j.hill on 2005-08-30
> Linux is not Unix. It is a copy of a Unix, Minix.

OK, but if it's a copy of a Unix, then it's a Unix too, right?

> Ubuntu is a desktop OS. It uses Linux as its kernel. It is a "real" Linux OS. It uses other tools in the Gnu system, that system includes Linux:

OK, this explains a lot.  I've never understood why Stallman gets so het up about nomenclature, until now.

---

### Post by grim42 on 2005-08-30
> OK, but if it's a copy of a Unix, then it's a Unix too, right?

No. What he means is that it's a clone of Unix... it doesn't use any Unix source code, but it's designed to work like a Unix system.

---

### Post by az on 2005-08-30
The "stack":

Application
Desktop Environment
Window Manager
Xserver
Userspace Tools
Kernel



Examples:

Application:  The Gimp, Mozilla-firefox, Tetris.
Desktop Environment:  Gnome, KDE, XFCE4 (This part *can* be omitted, commonly, when running a lightweight desktop)
Window Manager: Metacity, KDesktop, Icewm, Fluxbox..
Xserver:  Xfree86, Xorg, Mac X server- I forget the name)
Userspace tools:  GNU, BSD Unix, SCO Unix, Solaris Unix.
Kernel:  Linux, FreeBSD, NetBSD, OpenBSD, Darwin, Solaris, ....



Mix'n'match.

---

### Post by N'Jal on 2005-08-30
> No. What he means is that it's a clone of Unix... it doesn't use any Unix source code, but it's designed to work like a Unix system. 

Yeah very well put, basically Linus used minix but felt it was lacking so copied the functionality of minix by writing his own kernel code, and the rest as they say, is history.

---

### Post by Nu-Buntu on 2005-08-30
[QUOTE=j.hill]OK, but if it's a copy of a Unix, then it's a Unix too, right?[QUOTE]

Or so Darl at SCO would like us to believe.

---

### Post by j.hill on 2005-08-31
[QUOTE=N'Jal]Yeah very well put, basically Linus used minix but felt it was lacking so copied the functionality of minix by writing his own kernel code, and the rest as they say, is history.[/QUOTE]

So perhaps he should have called it Mimix.

---

