---
title: "A clean install of Arch, what to do now...."
date: 2008-12-12
forum: Arch and derivatives
---

### Post by gjoellee on 2008-12-12
I have installed Arch Linux successfuly and set up a user, it is time to install the desktop I want (xfce), but i somehow can't. I am at the command line adding the following command:
```
pacman -S xfce4
``` and I get this output:
> error: 'xfce4' : not found in sync dbwhat can I do? (I still only have the command line)

(I am totally new to Arc and have not used it before)

---

### Post by geirha on 2008-12-12
This is the Ubuntu forums. Ubuntu is a different distribution of linux than Arch Linux, and uses a different package management system. It is likely you will get a quicker and better response at Arch Linux's forums: [http://bbs.archlinux.org/](http://bbs.archlinux.org/)

---

### Post by Sorivenul on 2008-12-12
This should probably be in the Other OS Talk, Arch subforum.  
Make sure you update your system and package database before trying to install Xfce using:
```
pacman -Syu
```
This will update your system and get the current list of packages from Arch.  Usually a necessary step on a clean install.

---

### Post by geirha on 2008-12-12
> **Sorivenul said:**
> This should probably be in the Other OS Talk, Arch subforum.

Thanks, didn't know there was a forum for other OSes here.

---

### Post by Sorivenul on 2008-12-12
In the meantime, don't repost.  This will get moved, just give it some time.

---

### Post by bodhi.zazen on 2008-12-12
In general, the arch wiki is a good starting place :)

[http://wiki.archlinux.org/index.php/Xfce](http://wiki.archlinux.org/index.php/Xfce)

---

### Post by crimesaucer on 2008-12-12
The command you want is:

```
pacman -S xfce4 xfce4-goodies gtk2-themes-collection esound
```



Read about GDM's: [http://wiki.archlinux.org/index.php/GDM](http://wiki.archlinux.org/index.php/GDM)
for Slim: [http://wiki.archlinux.org/index.php/SLIM](http://wiki.archlinux.org/index.php/SLIM)


If you want SLIM (instead of GDM) to Login, then run this command:

```
pacman -S slim slim-themes
```


.... and then add "exec startxfce4" to you ~/.xinitrc file:

(As a regular user..... NOT AS ROOT)

```
nano ~/.xinitrc
```

then add this to the empty file:

```

#!/bin/sh

#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#

exec startxfce4

```

Save with "ctrl + o" "enter" "ctrl + x"


Next you will have to edit you /etc/inittab (in root), so follow this part: [http://wiki.archlinux.org/index.php/GDM#Inittab_Method](http://wiki.archlinux.org/index.php/GDM#Inittab_Method)

---

