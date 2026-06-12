---
title: "FATAL: Module fglrx is in use."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by rafaelxc on 2007-10-23
Hello Guys,
I trying to reinstall beryl but when I try to go over the guide, I'm getting stuck on the step of disabling the fglrx.
I'm getting this message:
FATAL: Module fglrx is in use.

when i make the sudo modprobe -r fglrx

Any one have some idea on how to bypass this?

Thanks

---

### Post by kellemes on 2007-10-23
Kill X first..
So do this from the console.

---

### Post by rafaelxc on 2007-10-23
how do i kill X? lol

---

### Post by kellemes on 2007-10-23
Try pressing Ctrl+Alt+F1, then login and type "sudo killall gdm".
**or**
Reboot and select the single-user or safemode or something like that.. forgot how it's called on Ubuntu. :popcorn: This will bring you to console.. login and do your thing..

---

### Post by rafaelxc on 2007-10-23
> **kellemes said:**
> Try pressing Ctrl+Alt+F1, then login and type "sudo killall gdm".
**or**
Reboot and select the single-user or safemode or something like that.. forgot how it's called on Ubuntu. :popcorn: This will bring you to console.. login and do your thing..

Thanks!!!

---

