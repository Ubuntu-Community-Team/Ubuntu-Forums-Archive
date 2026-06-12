---
title: "USB pen"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by ph7klw on 2006-06-09
Do you know how to install a USB pen into  Linux system?

---

### Post by Brynster on 2006-06-09
Strange question

Have you tried plugging it in? most USB ram drives are automatically detected and work perfectly.

Failing that on older ones i find booting the PC up with it already plugged in picks it up.

Thats about as techie as i get,

---

### Post by u.b.u.n.t.u on 2006-06-09
This might sound like a wise-guy reply, but you just plug it in. ubuntu should be able to read a usb pen. Unless you are asking a different question?

---

### Post by patrick295767 on 2006-06-09
You should set up/check your /etc/fstab:
unplug then replug the usb key, then 
  use sudo dmesg to know  which /dev/usb ... it'll be ... 
  or sudo qtparted 
...

---

