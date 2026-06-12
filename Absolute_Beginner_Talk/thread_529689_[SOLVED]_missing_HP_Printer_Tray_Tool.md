---
title: "[SOLVED] missing HP Printer Tray Tool"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by psyopper on 2007-08-19
Hello all,

I've been an Ubuntu 7.04 user for about 4 months now, darned near exclusively even though I kepp XP around for the wife. 

I have an HP PSC-1310 installed properly using hp-setup. CUPS finds it, I can print to it, etc. At one point following the hp-setup I had an icon in my tray that was a little purple "HP" that was a shortcut to a nice little utility for using my multi-function printer/scanner. 

About a week ago I was having panel problems so I xkilled the panel. When it regenerated the HP tray icon/tool was gone and I haven't seen it since. It was really convenient to be able to manage print jobs, scan jobs, and printer quality/ink/paper settings.

Does anyone else know what I'm talking about? More importantly, can someone point me in the right direction in getting that handy tray icon back?

Thanks in advance!

---

### Post by Happy_Man on 2007-08-19
Have you tried running hp-setup again, and rooting around to see if you can find it? Have you tried removing the notification applet from the panel and putting it back?

---

### Post by gn2 on 2007-08-19
You're looking for the HPLIP (HP Linux Imaging and Printing) toolbox.
.
You can create a Desktop Icon for it, right click, create launcher, type HPLIP and it will show the required set-up underneath, click on it then click create.

You will now be able to open the toolbox.
.
To get this in the panel right click in the System Tray, "Add" and duplicate the  entries found in the desktop icon's Properties (by right-click then Properties)

**EDIT** Or open the desktop launcher in a text editor and it will tell you the Exec command and the Icon.

Command: /usr/bin/hp-toolbox
Icon: /usr/share/pixmaps/hp-logo.xpm

---

### Post by psyopper on 2007-08-19
> **gn2 said:**
> You're looking for the HPLIP (HP Linux Imaging and Printing) toolbox.
.

Command: /usr/bin/hp-toolbox
Icon: /usr/share/pixmaps/hp-logo.xpm

Perfect, thank you very much!

---

### Post by gn2 on 2007-08-20
There is another HP logo to use as the icon, /usr/share/pixmaps/HPmenu.xpm
This may be the one you referred to before, it's blue/purple-ish and circular.

---

