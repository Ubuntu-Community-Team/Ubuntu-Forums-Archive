---
title: "New update"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by whoosh on 2006-09-14
The new update broke my linux.  It won't let Xserver start up and it says that there's some fatal error.  Is there anyway I can revert these changes or does anyone know how I can fix this?

---

### Post by szr4321 on 2006-09-14
I've got the same problem. At least I can supply some more information: The nvidia module can't be loaded, dmesg output: "nvidia: disagrees about version of symbol boot_cpu_data". Hopefully there'll be a driver update soon.
At the moment in /etc/X11/xorg.conf in the "Device" section I changed
Driver         "nvidia"
to
Driver         "nv"
I won't have hardware acceleration then, but at least I can start X.

---

### Post by charles.g.moore on 2006-09-14
if you have 10.3 you should read the sticky at the top of the page...
I think it also says some stuff about the update to 10.4 and how it can break things too...

---

### Post by szr4321 on 2006-09-14
@charles.g.moore: thanks, but it's the 10.4 version unfortunately.
This [post]("http://www.ubuntuforums.org/showthread.php?t=257353") seems related.

---

### Post by saz on 2006-09-14
i have the same problem

---

