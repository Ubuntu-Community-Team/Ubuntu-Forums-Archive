---
title: "Steam"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by MFerrante713 on 2007-09-04
I'm trying to install steam on Wine so I can download Garry's mod, but I'm still new to wine and can't figure out what to do. From what I understand so far, I need to go into winecfg select applications then add applications, but the file, Steam.msi, isn't appearing on the select an executable file list.

---

### Post by MFerrante713 on 2007-09-04
Maybe I need to install microsoft installer on wine before i can install .msi files?

---

### Post by supersonicdarky on 2007-09-04
```
wine msiexec /i SteamInstall.msi
```

---

### Post by MFerrante713 on 2007-09-04
Thanks a bunch!

---

### Post by MFerrante713 on 2007-09-04
now ive gota problem with the installer, i cant read anything on it, its blank?

---

### Post by MFerrante713 on 2007-09-04
Acctually its with steam itself, not the installer, it doesnt show anything, I can't register because I can't see what the buttons say.

---

### Post by Tomosaur on 2007-09-04
It's probably not worth the effort, but as ever, it's your choice. Last time I tried any HL2 game on Linux, it ran slowly and looked horrible.

Anyway - there are various ways to fix the problem. It's worth checking the comments on this bug page. Scroll right to the very bottom, the last comment supposedly works well - but there are a few more fixes in other comments:

[http://bugs.winehq.org/show_bug.cgi?id=4449](http://bugs.winehq.org/show_bug.cgi?id=4449)

---

### Post by splintercellguy on 2007-09-04
Steam and some Steam games work great on Wine. What version are you running, and have you looked at the Wine AppDb?

---

### Post by MFerrante713 on 2007-09-04
I'm not sure, nor do I know how to check, I'm somewhat new to linux and wine.

---

### Post by isaacj87 on 2007-09-04
Download the tahoma font.

Navigate to /home/yourname/.wine/drive_c/windows/fonts

put the tahoma font in there and you should be able to see the text in Steam now.

---

### Post by MFerrante713 on 2007-09-04
done, thanks

---

### Post by isaacj87 on 2007-09-04
It worked? That's good because I thought I left a step out!

:lolflag:

---

