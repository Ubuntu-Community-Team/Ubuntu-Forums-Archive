---
title: "xorg problems, unable to get into Ubuntu"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by forcesofhabit on 2006-09-23
I tried configuring my video card with the via drivers for the xserver. I changed one of the lines from "vesa" to "via". Now I get an error and a program shows me the output and what not.

How can I edit /etc/x11/xorg.conf from the command line and change the line back to what it was before???

:confused:

---

### Post by Orestes on 2006-09-23
```
sudo nano -w /etc/X11/xorg.conf
```

or failing that:

```
sudo dpkg-reconfigure xserver-xorg
```

HTH

---

### Post by decoherence on 2006-09-23
in the output xorg gives you, the first line that starts with (EE) is usually what the problem is.

---

### Post by davec64 on 2006-09-23
I did something similar!

I think you need

sudo gedit /etc/x11/xorg.conf

You should be able to edit back to the original in the terminal then. Always a good idea to make a backup of the original and just copy it back when things go wrong!

---

