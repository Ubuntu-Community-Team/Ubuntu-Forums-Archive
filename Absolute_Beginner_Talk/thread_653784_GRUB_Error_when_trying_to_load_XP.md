---
title: "GRUB Error when trying to load XP"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Matekking on 2007-12-30
Hi, I have a problem with dual-booting Win XP with Ubuntu 7.10, when trying to start XP with this menu.lst configuration: ```
http://paste.ubuntu-nl.org/49973/
```it gives an error 13 : Invalid or unsupported executable format, when trying to start with the "built-in" Win entry, it gives an error 21 : Selected disk does not exist
fdisk gives out this:```
http://paste.ubuntu-nl.org/49974/
```

---

### Post by Fixman on 2007-12-30
> **Matekking said:**
> Hi, I have a problem with dual-booting Win XP with Ubuntu 7.10, when trying to start XP with this menu.lst configuration: ```
http://paste.ubuntu-nl.org/49973/
```it gives an error 13 : Invalid or unsupported executable format, when trying to start with the "built-in" Win entry, it gives an error 21 : Selected disk does not exist
fdisk gives out this:```
http://paste.ubuntu-nl.org/49974/
```

In what hard disk and in what partition is your XP stored?

---

### Post by Matekking on 2007-12-30
> **Fixman said:**
> In what hard disk and in what partition is your XP stored?

I have only one hard drive, plus a pendrive which I can't mount in linux, but smart Windows assigned "C:\" to it

On the winchester I have an ext3 first, a swap 2nd, and the last partition is XP's

Edit:GRUB can load a mini-windows from the pendrive with the builtin entry

---

### Post by Fixman on 2007-12-30
> **Matekking said:**
> I have only one hard drive, plus a pendrive which I can't mount in linux, but smart Windows assigned "C:\" to it

On the winchester I have an ext3 first, a swap 2nd, and the last partition is XP's

Edit:GRUB can load a mini-windows from the pendrive with the builtin entry

If you want to boot windows from the hard drive, write _at the end_ of /boot/grub/menu.lst the following:

```

title Windows XP
root (hd0,2)
chainloader +1

```

---

### Post by Fixman on 2007-12-30
Did it work?

---

### Post by Matekking on 2007-12-30
Wow, it worked, really thanks!

---

