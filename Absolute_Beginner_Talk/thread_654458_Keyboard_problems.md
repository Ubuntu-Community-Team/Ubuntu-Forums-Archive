---
title: "Keyboard problems"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by quadrantids on 2007-12-31
I have a French Dell Latitude with dual boot Windows Ubunutu. When Ubuntu boots the keyboard seems to be qwerty. From System/Preferences/Keyboard I have "added" a new keyboard: French,  Generic 105 Key (Intl) PC and made this my default (which corresponds to my Latitude's inbuilt keyboard).

Despite this whenever I boot Ubuntu, it starts with a qwerty layout (which was awkward for passwords until I realized what was going on). I usually then (often but not always) have to go System/Preferences/Keyboard to confirm the French layout.

Is there any way I can make Ubuntu boot in azerty layout?

Thanks in advance.

---

### Post by ray bot on 2007-12-31
I think this has to be changed in /etc/X11/xorg.conf.  Open that file like so ```
gksudo gedit /etc/X11/xorg.conf
```
Look for the line that contains Option "XkbLayout" "something", and change it to Option "XkbLayout" "fr-latin9"
After that, save the file and reboot.  That should either fix the problem or cause your computer to explode.  I'll keep my fingers crossed for you.

---

