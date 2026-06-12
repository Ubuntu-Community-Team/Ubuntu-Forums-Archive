---
title: "Grub carsh issue"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-01-30
hello all 

i installed kubuntu and i donot like it so u want to back to ubuntu .......... 

i delete the partations of the installation from Xp and i start downloading ubuntu again from xp but when i made restart i found that grub crashed :( what i can do to get back to Xp                 >> i had the kubuntu CD <<

---

### Post by istrebitjel on 2007-01-30
Check out this documentation on grub:
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC14](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html#SEC14)
You can boot your kubuntu cd and from the prompt boot windows.

---

### Post by igknighted on 2007-01-30
For future reference:

1) If you didnt like it and wanted to reinstall, windows doesnt manage linux partitions well at all, so that was a a very dangerous way of doing it.  You could have just downloaded Ubuntu w/ gnome and installed to the same partitions.

2) Even easier, ```
aptitude remove kubuntu-desktop
aptitude install ubuntu-desktop
```
would accomplish the same thing without a reinstall.

---

