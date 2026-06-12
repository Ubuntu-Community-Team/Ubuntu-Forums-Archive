---
title: "Nano in Ubuntu Desktop Live CD Rescue a broken system"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by .neo on 2008-02-13
My Ubuntu freezes upon boot because of what I suspect is the wrong entry in GRUB's menu.lst file... I'd like to edit the menu.lst file but when I boot from a Desktop Live CD using "Rescue a broken system" entry I can't start nano to edit that file (even though I can list its content with cat though). The error is: ```
Error openning terminal: bterm.
```
Anyone knows how to start nano or any other command line editor in that mode, plz?!?

TIA

---

### Post by jan quark on 2008-02-13
try 

```
gksudo gedit /path/to/file
```

---

