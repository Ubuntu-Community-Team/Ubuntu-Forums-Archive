---
title: "Input problem: can't type tilde(shift-`) and eks(uvw?yz) keys"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by dansei on 2007-04-09
I can't type the tilde ("?" can't type here) character and letter (eks, uvw?yz), when I pressed the tilde key, whatever I hold shift or not, only "`" appears. And when I pressed the (eks) key, nothing appears (the keyboard is ok, no hardware problem).

Edgy 6.10
Keyboard modeL: Generic 105-key (Intl) PC
Selected Layout: U.S. English

Thanks
Lenik

---

### Post by terdon on 2007-04-09
Have a look at the /etc/X11/xorg.conf file, there is a section called keyboard, do you have the right keyboard model there?

---

### Post by Hieronymus on 2007-04-09
Did you try to goto system >> preferences >> keyboard ??

Jeroen

---

### Post by TravisNewman on 2007-04-09
Have you tried a different keyboard?

---

