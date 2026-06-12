---
title: "GRUB editing"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by dingo-linux on 2007-06-12
Hello! I'm completely new to Ubuntu, and Linux in general. I'm hoping somebody will be able to help me. I want to make the timeout in GRUB longer (currently is 10 sec). I know I have to go to boot/grub/menu.lst, and edit it as root. When I do that it won't let me save, because I don't have privileges, but it won't let me log in as root(if I'm not mistaken I can't log in at user selection, only in terminal), so how do I do it? Any help is appreciated. Thnx in advance.

---

### Post by adityakavoor on 2007-06-12
type in terminal 
```

sudo gedit /boot/grub/menu.lst

```

change the time there ..

---

### Post by mcduck on 2007-06-12
to open the file for editing as root, open a terminal and run the following command:

in Gnome: 'gksudo gedit /boot/grub/menu.lst'
in KDE: 'kdesu kate /boot/grub/menu.lst'
in command line: 'sudo nano /boot/grub/menu.lst'

---

### Post by southernman on 2007-06-12
In a terminal type:

> gksudo gedit /boot/grub/menu.lst

I don't think you can set it to more than 10 seconds, but give it a shot anyway.

Wait, are you talking about the grub splash screen, or the option to hit "ESC" to get into the splash screen?

If it's the first, then hitting any key will stop the countdown. Glare at it as long as ya like... ;)

---

### Post by drowner on 2007-06-12
I assume you are using Ubuntu (not Kubuntu....)

open a terminal and type:

gksudo gedit /boot/grub/menu.lst

the gksudo command will let you run a graphical application as root when you enter your password.

gedit is a graphical text editor.

---

### Post by tommcd on 2007-06-12
Ubuntu uses sudo to gain root privlidges, so it would be "gksudo gedit /boot/grub/menu.lst". The "gk" before sudo is sometimes recomended for launching programs with a GUI. And gedit is a text editor with a GUI. 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
As for editing grub menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#timer](http://users.bigpond.net.au/hermanzone/p15.htm#timer)
And welcome to the forums!
EDIT: wow you guys are fast! there were no replies when I started typing.

---

### Post by dingo-linux on 2007-06-12
Thanks! That was fast, I'll try it.

---

