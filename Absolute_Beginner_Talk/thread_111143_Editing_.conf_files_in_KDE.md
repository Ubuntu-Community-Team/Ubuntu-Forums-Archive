---
title: "Editing .conf files in KDE"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by equal on 2006-01-01
Hey guys, I'm not really a Linux noob, but KDE is a whole new ballgame for me. I've always found the best way for me to learn is to throw myself in headfirst, so I reformatted and only installed the Kubuntu KDE.

My question is, I'm trying to edit the xorg.conf file, and until now, the command I used in Gnome was always
```
 sudo gedit /etc/X11/xorg.conf
```

now I get the error
```
sudo: gedit: command not found
```

I figure gedit is probably a gnome command or something. So what do I do now?

---

### Post by Swab on 2006-01-01
sudo kate /etc/X11/xorg.conf

gedit is a gnome app.. kde has kate!

---

### Post by kingsidy on 2006-01-01
gedit is the default text editor for gnome. For kde i think that it is kate. There is also pico. so at the terminal type in > sudo kate /etc/X11/xorg.conf or > sudo pico /etc/X11/xorg.conf

---

### Post by iand675@gmail.com on 2006-01-01
use either kwrite or kate

---

### Post by equal on 2006-01-01
Merci, my friends. I knew it was a simple thing!

I thought about switching to Debian recently, but the thing that keeps me on Ubuntu is this wonderful community. You are all so helpful!

---

### Post by equal on 2006-01-01
uh oh! I tried it and got this:
```
phil@ubuntu:~$ sudo kate /etc/X11/xorg.conf
Password: ********
Error: "/var/tmp/kdecache-phil" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
```

---

### Post by Adrian on 2006-01-01
If you run into problems sudo:ing kate, use "kdesu" instead of "sudo".

kwrite and kedit (I don't think it's installed by default, though) are nice editors also. 

If you'd rather want to use gedit and don't mind to use some Gnome libraries, it's totally possible to install it from Adept/Synaptic.

---

### Post by Adrian on 2006-01-01
[QUOTE=equal]uh oh! I tried it and got this:
```
phil@ubuntu:~$ sudo kate /etc/X11/xorg.conf
Password: ********
Error: "/var/tmp/kdecache-phil" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
```[/QUOTE]

Try this instead:
```
kdesu kate /etc/X11/xorg.conf
```

---

