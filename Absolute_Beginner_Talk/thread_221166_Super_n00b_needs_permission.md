---
title: "Super n00b needs permission"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Bumblescrump on 2006-07-22
Hey, I'm really new at computers in general, and I can't figure out why I don't have permission to change the text in the default display manager, I was trying out KDE, which I wasn't happy with, but I accidently set it as the default.  

If you reply, just remember your talking to a very inexperienced computer user.

---

### Post by scxtt on 2006-07-22
what ever you want to do, preface it by sudo - if it's owned by root {the account that's considered the 'Administrator':
[indent]gksudo gedit /etc/X11/default-display-manager[/indent]

[size=4]&#8593;&#8593;[/size] assumes you're using gnome, but there is a kde equivalent [size=4]&#8593;&#8593;[/size]
[indent]kdesu kate /etc/X11/default-display-manager[/indent]enter either of those in a terminal and enter YOUR password.

---

### Post by srunni on 2006-07-22
@ scxtt:

I'm pretty sure that you don't have to gksudo or kdesu, you can just regular old sudo and it will do the same thing.

---

### Post by scxtt on 2006-07-22
that's true, but it's "better" to use gksudo/kdesu when opening a GUI program that's not a terminal based program (as in vi or nano) ...

gksudo gedit /etc/X11/xorg.conf
sudo vi /etc/X11/xorg.conf

---

### Post by Bumblescrump on 2006-07-22
Hey, that worked, thanks.

---

