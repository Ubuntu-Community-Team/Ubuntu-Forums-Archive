---
title: "blank screen"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by STEVE2493 on 2008-03-25
hi
just installed ubuntu for the first time, ive changed some setting's for the graphics to use dual monitors on my ati 9550 when i rebooted i just get a blank screen on both screens, can i revert back some how?

cheers

---

### Post by joshrobinson on 2008-03-25
try holding ctrl+alt and hitting f1 to see if you can get to a terminal and run this command

```

sudo dpkg-reconfigure -phigh xserver-xorg
```

if you cant get to a terminal, restart, and enter the grub menu when it says to hit a certain button, then go into recovery mode, then run the code i posted

---

### Post by Helgiks on 2008-03-25
$ sudo dpkg-reconfigure -phigh xserver-xorg

Try that.

---

### Post by STEVE2493 on 2008-03-25
cheers

---

