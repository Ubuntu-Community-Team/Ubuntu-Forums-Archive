---
title: "tty font size or 132 col"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by babs on 2006-01-04
Hello,

I'm trying to configure my tty and console terminal (Not the Xterm) about font size or/and to work with 132 columns.
Could help me to find the right way?!

Thanks

babs

---

### Post by benplaut on 2006-01-04
I'm not quite sure how to do it, but you might find something by searching for 'framebuffer'

it involves adding something similar to vga=771 to your /boot/grub/menu.lst, but **don't take my word for it**!

Good Luck!

---

### Post by piedamaro on 2006-01-05
You need a 'vga=' parameter at your kernel command line in /boot/grub/menu.lst
Try vga=792 (it changes the resolution not font size or dpi)

---

### Post by babs on 2006-01-10
Thank's all.

It seems to be the good way by changing the Grub menu.

Regards.

Babs

---

