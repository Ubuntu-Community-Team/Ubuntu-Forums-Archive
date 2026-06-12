---
title: "Does this run on virtual PC ?"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by sarthor on 2005-06-21
Hi all,

Does UbuntuLinux run on Microsoft VirtualPC?

---

### Post by somuchfortheafter on 2005-06-21
yes

---

### Post by Diego F. on 2005-08-10
[QUOTE=somuchfortheafter]yes[/QUOTE]
 I tried that, but the graphical interface didn't start. Any ideas?

---

### Post by Sam on 2005-08-10
Open /etc/X11/xorg.conf while in console mode, look for section "Screen", DefaultDepth, change value 24 to 16. Then restart X with [FONT=monospace]$ sudo /etc/init.d/gdm restart[/FONT]

---

### Post by ozzie123 on 2005-08-10
My friend also tried this and Kubuntu (he's installing KDE XWindow of course) failed to recognize his graphic card. Otherwise, Kubuntu works just fine without using Virtual PC.

---

### Post by ninor on 2006-02-22
[QUOTE=Sam]Open /etc/X11/xorg.conf while in console mode, look for section "Screen", DefaultDepth, change value 24 to 16. Then restart X with [FONT=monospace]$ sudo /etc/init.d/gdm restart[/FONT][/QUOTE]

I'm in the same situation, but if we cannot enter to the O.S, how can we go to the console?

Thanks

---

### Post by nickj6282 on 2006-02-23
Watch closely when booting the virtual Ubuntu machine and press ESC at the proper moment to boot into recovery mode.

---

