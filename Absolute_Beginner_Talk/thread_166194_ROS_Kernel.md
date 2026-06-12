---
title: "ROS Kernel?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-25
Hi,

I was wondering.. will it be possible to use the Reactos Kernel (when it is done), on Ubuntu? And would this make Ubuntu able to run windows apps and drivers, like Reactos?

[http://www.reactos.org/xhtml/en/index.html](http://www.reactos.org/xhtml/en/index.html)

Thanks :)

---

### Post by nocturn on 2006-04-26
I highly doubt it.

ReactOS is a reimplementation of the Windows API's so that Win32 apps work on it.

Linux is a POSIX compliant system, which is quite different from that model, so the kernel of one is not interchangable with the other.

---

### Post by buu700 on 2007-12-06
[http://en.wikipedia.org/wiki/POSIX#POSIX-oriented_operating_systems](http://en.wikipedia.org/wiki/POSIX#POSIX-oriented_operating_systems)

Actually, the NT kernel is POSIX-compliant. According to Wikipedia, it is "Fully" compliant, whereas Linux and BSD are "Mostly" compliant...
Maybe once the React kernel hits beta we'll see some React-based dstributions:popcorn:.

EDIT: Also, [http://www.reactos.org/wiki/index.php/POSIX_Subsystem](http://www.reactos.org/wiki/index.php/POSIX_Subsystem) and [http://www.reactos.org/wiki/index.php/PSX](http://www.reactos.org/wiki/index.php/PSX).

---

### Post by aktiwers on 2007-12-07
Thanks for the links! That would indeed be cool!

---

