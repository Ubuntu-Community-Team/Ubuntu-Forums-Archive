---
title: "How do I get the Mac Keyboard working like...?"
date: 2011-10-22
forum: Apple Hardware Users
---

### Post by jmate24 on 2011-10-22
...it does on a Mac? with the Command, Function (fn), F1-F19, and keyboard shortcuts working like it does on a Mac?
I am using a PC and I would like to set up my mac keyboard to work like it does on a mac. instead of working like a pc keyboard (layout and shortcuts).

---

### Post by jerrycal on 2011-10-22
> **jmate24 said:**
> ...it does on a Mac? with the Command, Function (fn), F1-F19, and keyboard shortcuts working like it does on a Mac?
I am using a PC and I would like to set up my mac keyboard to work like it does on a mac. instead of working like a pc keyboard (layout and shortcuts).


To swap the fn key functionality like on Mac edit /etc/pommed.conf and set the variable fnmode to 2, or add this line to /etc/modprobe.d/options: 
options hid_apple fnmode=2

---

### Post by jmate24 on 2011-12-15
I just bought a Mac Mouse today and I would like to make it work like a Mac Mouse along with my Mac Keyboard.

---

