---
title: "Window Managers and Desktop question."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by nightrider.36 on 2007-06-29
Hello all--I'm new to the Ubuntu world.  I'm really confused about the differences between GNOME or KDE and a Window manager, what is it?

Also, if I want to try other window managers like TWM, motif, IceWM, BLackbox--how do I do this using Ubuntu. 

Many years ago, I used to type "startx" or something like that in RHAT.  But in Ubuntu I can't figure out how to log in to line command mode so that I can try other Window managers.

Any help is appreciated, thanks.:D

---

### Post by chamberlain2006 on 2007-06-29
Nowadays, you don't need to use command line to login.  On the main login screen, click options, and sessions, to choose which one to load.  There are quite a few WM's in the repositories I believe.  Gnome, KDE, and XFCE are there for sure, but I also remember some others.  If it's in the repository, you can install it in Synaptic.  If not, you may need to download it from the projects web site.  The install process will vary for these ones.

---

### Post by Rui Pais on 2007-06-29
Gnome and kde are [Desktop environments]("http://en.wikipedia.org/wiki/Desktop_Environment").
Gnome, as an example, use metacity as a [Windows Manager]("http://en.wikipedia.org/wiki/Window_Manager")... Or can use compiz/beryl/fusion.

You can install other DE or WM with apt. (search with synaptic). 
After install, logout and in your login manager (gdm/kdm) choose Session and you can choose the DE/WM you want to boot to.

To use the startx you need to kill your running X server with the login manager.
Login on a console (Ctrl+Alt+F1/6) type:
```
sudo /etc/init.d/gdm stop
```
and then startx.

---

### Post by zach12 on 2007-06-29
i would use kde or gnome

---

### Post by nightrider.36 on 2007-06-29
That's where I'm having the problem. When I select sessions, the only option I get is XFCE but none of the other Window managers that I installed through synaptic.  Is there a setting somewhere that will allow me to see all the other WMs that I've installed?

thanks.

> **chamberlain2006 said:**
> Nowadays, you don't need to use command line to login.  On the main login screen, click options, and sessions, to choose which one to load.  There are quite a few WM's in the repositories I believe.  Gnome, KDE, and XFCE are there for sure, but I also remember some others.  If it's in the repository, you can install it in Synaptic.  If not, you may need to download it from the projects web site.  The install process will vary for these ones.

---

### Post by Rui Pais on 2007-06-29
for the DE you need meta packages:
```
sudo apt-get install ubuntu-desktop
```
or
```
sudo apt-get install kubuntu-desktop
```

for WM only a simple package like
```
sudo apt-get install fluxbox
```
(use synaptic to search)

Less main stream DE (like e17) and WM  (like compiz) require more trouble... 
theres a lot of how-to on this forum.

---

### Post by deGz0rx on 2007-07-07
hey guys, its maybe offtopic but i dont understand this
when do i use synaptic or ordinary "add/remove" ?
whats the difference?

thnx :)

---

