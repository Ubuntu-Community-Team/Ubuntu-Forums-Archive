---
title: "5 button mouse"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by MasDom on 2007-07-29
Hi,

I am absolutely new to Ubuntu and to Linux so my question might sound a bit stupid. I found [this]("http://ubuntuforums.org/showthread.php?t=28374&highlight=5+button+mouse") thread in the ubunto forum. I tried to edit the xorg.conf file but I couldn't save my edits. What did I do wron? I opened the file by double klicking.

Thx alot in advance

MasDom

---

### Post by Songwind on 2007-07-29
the place that xorg.conf resides is owned by root so you can only write there if you sudo

you can open it in a way that will let you edit it by pressing Alt-F2 and running this command:
```
gksudo gedit /etc/X11/xorg.conf
```

---

