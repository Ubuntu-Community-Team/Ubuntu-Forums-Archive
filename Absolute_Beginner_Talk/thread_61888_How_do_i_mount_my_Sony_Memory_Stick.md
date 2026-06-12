---
title: "How do i mount my Sony Memory Stick?"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-09-02
On Ubuntu Hoary?

---

### Post by aysiu on 2005-09-02
[QUOTE=Muhammad]On Ubuntu Hoary?[/QUOTE] It should automount.

---

### Post by Muhammad on 2005-09-02
But it didn't. :(

---

### Post by parktownprawn on 2005-09-02
[QUOTE=Muhammad]On Ubuntu Hoary?[/QUOTE]

What hardware are you trying to use to mount the memory stick ?

A USB card reader ?

---

### Post by Muhammad on 2005-09-02
[QUOTE=parktownprawn]What hardware are you trying to use to mount the memory stick ?

A USB card reader ?[/QUOTE]

Nop, I'm using an optical Sony mouse.

---

### Post by parktownprawn on 2005-09-02
[QUOTE=Muhammad]Nop, I'm using an optical Sony mouse.[/QUOTE]

whats the model? (it helps when you post as much detail as possible)

many usb card readers work out of the box with ubuntu but I don't know about mice with inbuilt card readers.  sounds like something like that would require special drivers. 

you might be able to find some info on  google or maybe [http://www.linuxcompatible.org/compatibility.html](http://www.linuxcompatible.org/compatibility.html)

---

### Post by poofyhairguy on 2005-09-02
[QUOTE=Muhammad]Nop, I'm using an optical Sony mouse.[/QUOTE]

That confused me like no other.

---

### Post by az on 2005-09-02
Type 
sudo tail -f /var/log/messages
in a terminal before you plug the thing in for the first time after booting.

Actually, do the obvious and plug the thing directly into your computer, first.  Post the output of that, then post the output of tail -f /var/log/messages when plugging it up your mouse.

---

### Post by xmastree on 2005-09-02
[QUOTE=azz]Actually, do the obvious and plug the thing directly into your computer,[/QUOTE]I don't think that's possible. A Sony memory stick isn't a usb drive, it's a memory card, similar to SD etc. His mouse must have a built-in card reader.

---

