---
title: "Install after booted from a bootable stick"
date: 2015-11-16
forum: Any Other OS
---

### Post by APUboard on 2015-11-16
I just booted a micro core Linux with a bootable usb stick.
Now, I would like to get it on the msata with the application tc-install.sh. But I have to give it the core.gz and the vmlinuz but I can see these files when I open it on Windows, but after I booted I can't locate them on the usb stick.
**What are my options to install it on the msata?**
Since I'm connecting over serial I can't just download one with wget.

---

### Post by TheFu on 2015-11-16
Welcome to the Ubuntu Forums!

**Core Linux** isn't Ubuntu.  Perhaps you need to be in the "not-ubuntu" subforum?
Documentation for Tiny Core is here: [http://distro.ibiblio.org/tinycorelinux/](http://distro.ibiblio.org/tinycorelinux/)
Video of installation: [https://www.youtube.com/watch?v=0QMY3V5XLj8](https://www.youtube.com/watch?v=0QMY3V5XLj8)
Instructions for non-networked users: [http://gr8idea.info/os/tutorials/tiny-core/microcore.html](http://gr8idea.info/os/tutorials/tiny-core/microcore.html)

For any lurkers, MicroCore Linux doesn't have a GUI, so it isn't usually something most users here would want.  

Also, there is another OS, linux-based, also calling itself "Core" ... so I'm assuming the tc-install.sh means it is from the "TinyCore Linux" guys.  TinyCore doesn't install the way that Debian, Ubuntu, ... install.  The entire OS is located inside a gzip file (or multiple gz files) with all the directories, permissions, users, programs inside it too. At runtime, that file gets expanded into RAM and run.

---

### Post by howefield on 2015-11-16
Thread moved to the "*Any Other OS* forum.

---

