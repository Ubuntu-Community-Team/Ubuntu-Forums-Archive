---
title: "I want to tripple boot"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-29
Ok so I want to tripple boot between Windows XP,Ubuntu 7.04 and Fedora 7 I have Windows and Ubuntu installed now so how would I reconfigure grub to show Fedora in the boot options.

---

### Post by wondering_jew on 2007-06-29
I'm not familiar with the fedora install but when it gets to the grub installation step on the installer it *should* detect which other OS's are on your computer and do that for you.

---

### Post by jonward0690 on 2007-06-29
Yea Fedoras grub is different I want to keep Ubuntus grub.

---

### Post by bodhi.zazen on 2007-06-29
LOL

Install Fedora

During the install install grub to the Fedora root partition

Add this to Ubutnu /boot/grub/menu.lst :

title Fedora 7
root (hdxy)
chainloader +1
boot

It you do not want to chainload then you will need to manually update the ubuntu grub ...

---

