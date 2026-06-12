---
title: "Minimal Installation Help"
date: 2013-05-02
forum: Any Other OS
---

### Post by Arashaun42 on 2013-05-02
Hello All!

I recently started a project to turn an old computer into a Retro game console using MAME.

I am at an end though as to which distro I should use.
I've tried TinyCoreLinux, and was pleased at how fast it booted, however I found it hard to setup and install properly, and has limited MAME support

Which distro would you suggest? I would preferably want one that is fast to boot, has minimal installed packages, and is able to support MAME, and gamepads (Specifically a wired and wireless Xbox controller)

Thank you

---

### Post by mips on 2013-05-02
What are the specs of the PC?

---

### Post by kiyop on 2013-05-03
Debian.
You should not install bloat desktop environment such as GNOME or KDE, at installation. Start network install with minimal business card iso or so and check **OFF ALL** at the tasksel (package selection step). After rebooting with the installed debian, you can install many packages as you like if your NIC is correctly used to connect to internet.

Debian has mame packages:
[http://packages.debian.org/search?keywords=mame](http://packages.debian.org/search?keywords=mame)

But, Debian (version 3.1 or later) does not support 80386 CPU.
[http://www.debian.org/releases/stable/i386/ch02s01.html.en#id583669](http://www.debian.org/releases/stable/i386/ch02s01.html.en#id583669)
[http://www.debian.org/releases/stable/i386/ch02s01.html.en](http://www.debian.org/releases/stable/i386/ch02s01.html.en)

---

