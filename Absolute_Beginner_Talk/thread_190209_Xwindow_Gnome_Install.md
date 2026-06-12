---
title: "Xwindow/ Gnome Install??"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by N3wtR0ckn13 on 2006-06-06
Problem: X window/ Gnome does not start
Tried:$ apt-get update, upgrade, startx, Xfree86, x-window-system etc.
AlsoTried: install on VmWare, and nothing
---------------------------------------------------------------------------
OS: clean install of Ubuntu Dapper Drake Server. 
---------------------------------------------------------------------------
Question: Does ubuntu dapper drake server not come with x window/ gnome install anymore?
---------------------------------------------------------------------------

---

### Post by nalmeth on 2006-06-06
Server install has never included a gui.
You've run a lot of command's that come really close to the ticket, but run this one:
sudo apt-get install ubuntu-desktop
or if you like kde replace ubuntu with kubuntu,
and if you like xfce, replace ubuntu with xubuntu

---

### Post by N3wtR0ckn13 on 2006-06-06
[QUOTE=nalmeth]Server install has never included a gui.
You've run a lot of command's that come really close to the ticket, but run this one:
sudo apt-get install ubuntu-desktop
or if you like kde replace ubuntu with kubuntu,
and if you like xfce, replace ubuntu with xubuntu[/QUOTE]


thanks. it helped. is ...install ubuntu-desktop strictly ubuntu or do other linux distros support this. normally, w/ debian anyways i install x-window, then gnome and/or kde. 

also, any idea on how i can resize the loading screens after the server starts up?

---

### Post by Flavian on 2006-06-06
Hey guys, here is my problem:
I set up Ubuntu on my laptop, after a little custom work on the graphics drivers it works all totally fine, but I want to try KDE and maybe XUbuntu as well, I tried to get it but it doesnt seem to work. Can somebody help me?
I am a total beginner...

florian@octavius:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

is all I got!
Thanks in advance
Flo

---

### Post by N3wtR0ckn13 on 2006-06-07
[QUOTE=Flavian]Hey guys, here is my problem:
I set up Ubuntu on my laptop, after a little custom work on the graphics drivers it works all totally fine, but I want to try KDE and maybe XUbuntu as well, I tried to get it but it doesnt seem to work. Can somebody help me?
I am a total beginner...

florian@octavius:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

is all I got!
Thanks in advance
Flo[/QUOTE]


so you installed ubuntu w/ gnome first and now you installed kde? try $startx. let me know.

---

### Post by N3wtR0ckn13 on 2006-06-07
[QUOTE=Flavian]Hey guys, here is my problem:
I set up Ubuntu on my laptop, after a little custom work on the graphics drivers it works all totally fine, but I want to try KDE and maybe XUbuntu as well, I tried to get it but it doesnt seem to work. Can somebody help me?
I am a total beginner...

florian@octavius:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

is all I got!
Thanks in advance
Flo[/QUOTE]

just finished installing kubuntu. i'm suprised, since i normally use gnome but i like what i see. kde does not load initially when you run apt-get install kubuntu-desktop. so $startx will prompt kde to run.

ps- though, if kde was not found you might looking at your partitioning of the drives and how you loaded ubuntu. howtoforge.com has a bunch of solid tutorials.

---

