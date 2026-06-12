---
title: "How to edit xorg.conf file...URGGGHHHH"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by kamaboko on 2007-02-17
Hi,

I'm trying to edit a few lines, but it isn't working.  I've tried the following

sudo gedit /etc/x11/xorg.conf

the text editor comes up w/the file.  i make my changes, but when i try to save it says i don't have rights.  

thanks,
k

---

### Post by dbbolton on 2007-02-17
did you try: gksudo gedit ~

---

### Post by aysiu on 2007-02-17
The proper command is ```
gksudo gedit /etc/X11/xorg.conf
``` Please also watch your case--it should be **X11**, not **x11**.

---

### Post by kamaboko on 2007-02-17
i just tried that now.  it gives me a blank text page w/out any of the other info from the xorg.conf file.  is that normal?

---

### Post by kamaboko on 2007-02-17
> **aysiu said:**
> The proper command is ```
gksudo gedit /etc/X11/xorg.conf
``` Please also watch your case--it should be **X11**, not **x11**.

thank you.  the devil is in the details.  i will not forget the big X next time....or will I? :)

---

### Post by aysiu on 2007-02-17
Can you do this, then?

Press Alt-F2 and type ```
gksudo nautilus
``` This will launch your file browser as administrator. Then navigate to the /etc/X11 directory

Look at any files that have xorg.conf in the name and edit the appropriate one.

---

### Post by tommcd on 2007-02-18
For safety (or if you're anal, like me) you should always backup any configuration file before you edit it. That way it can easily be restored if you screw it up. To back it up, do:
<sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.bak> The -i option means it will prompt you if you are overwriting an existing file. You don't want to do that either by mistake. Then if you need to restore it, you just do:
<sudo cp -i /etc/X11/xorg.conf.bak /etc/X11/xorg.conf> This will then ask you if you want to overwrite the existing xorg.conf, in which case you answer "y" since you are restoring the backup.

---

