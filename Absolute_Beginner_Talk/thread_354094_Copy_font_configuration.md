---
title: "Copy font configuration"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Ruth Lazkoz on 2007-02-05
Hi,

I have problems displaying some graphics in Mathematica. I have been exchanging some messages with the support service at Wolfram, but still haven't found a solution.

They do not experience the same problems as me, and on top of that I have tried my problematic notebook in a colleague's computer and the problem did not show up. This colleague's distro is Mandriva and runs KDE.

Is there I way I can make an exact copy of his font configuration? I use gnome+ubuntu edgy.

Thanks,

Ruth

---

### Post by Shatrat on 2007-02-05
You could try copying the /etc/X11/fonts and /usr/share/fonts and the Files section of his /etc/X11/xorg.conf
I think thats about all the X stuff relating to fonts, but it might be that you need to change a font path somewhere in your Mathematica config, and I dont really know anything about Mathematica.

---

