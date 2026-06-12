---
title: "Help with the Window Border"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by SIXAXIS on 2008-04-11
Hi,

I finally got Compiz Fusion installed on my ATI 200m (really hard to do) and I also installed Emerald. I couldn't figure out how to install a theme so I checked the internet. It said to choose the theme and type in 'emerald --replace' in a console. I did that and it worked, but as soon as I closed the console, the window borders went away. I can't get them back. I've open Emerald, tried the command, and tried the regular Ubuntu way. Can someone help me get my window borders back? I'm tired of pressing ALT+F4 to close.

---

### Post by spiderbatdad on 2008-04-11
try Alt-F2```
emerald --replace
```

---

### Post by joshrobinson on 2008-04-11
the best way to do this, is to use the fusion-icon

```
sudo apt-get install fusion-icon
```

now go to system > preferences > sessions

in there on the "startup programs" tab, click add
as the name put fusion-icon, and the same with the box that says command

now it will startup whenever your computer does

now use alt+f2 and type fusion-icon to open it for this session
it will be in your system tray, from here you can right click it and go to "select window decorator"
you can use this to switch to emerald or the GTK window decorator
you can also open ccsm, emerald theme manager, and reload compiz from here

also, i have an ATI 200m in my laptop, ive been running compiz on it since compiz started, when you had to compile it from source
when it was just compiz, or compiz-quinn.. its easier after the first time setting it all up

---

### Post by twist2b on 2008-04-11
deffinitly add to your sessions startup. THOUGH, I highly suggest NOT using emerald. I think its ugly. Use nautlius or w.e its called. under System>Prefrences> Appeareance
Get 7.10 if you can.
Recommend getting it through the update manager.

here is Mac4Lins themes:
[http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

---

### Post by spiderbatdad on 2008-04-11
> **joshrobinson said:**
> the best way to do this, is to use the fusion-icon

```
sudo apt-get install fusion-icon
```

now go to system > preferences > sessions

in there on the "startup programs" tab, click add
as the name put fusion-icon, and the same with the box that says command

now it will startup whenever your computer does

now use alt+f2 and type fusion-icon to open it for this session
it will be in your system tray, from here you can right click it and go to "select window decorator"
you can use this to switch to emerald or the GTK window decorator
you can also open ccsm, emerald theme manager, and reload compiz from here

also, i have an ATI 200m in my laptop, ive been running compiz on it since compiz started, when you had to compile it from source
when it was just compiz, or compiz-quinn.. its easier after the first time setting it all up

+1 fusion-icon

---

### Post by joshrobinson on 2008-04-11
> **twist2b said:**
> deffinitly add to your sessions startup. THOUGH, I highly suggest NOT using emerald. I think its ugly. Use nautlius or w.e its called. under System>Prefrences> Appeareance
Get 7.10 if you can.
Recommend getting it through the update manager.

here is Mac4Lins themes:
[http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

emerald has themes, it actually can be very good looking with a nice one
the screenshot below is using emerald

oh and gnome's window manager is metacity, nautilus is the GUI file manager

---

### Post by SIXAXIS on 2008-04-11
The fusion-icon doesn't work because it cant find the package. Maybe I have to add a source to the list of repositories (I think it's called that). I have universe and all of those enabled too. Oh yeah, I'm not using 7.04, I'm using 7.10 32-bit.

---

### Post by SIXAXIS on 2008-04-11
Okay, so the fusion-icon program didn't work. But I went into the Compiz Fusion (ccsm) control panel and enabled Window Decorations. This put on the Mac4Lin theme I enabled in Emerald. I like it, but what if I wanted to change it? How would I go back to using the regular Linux theme manager? Emerald seems like to much trouble for a little bit of eye-candy.

---

### Post by joshrobinson on 2008-04-11
hmm i didnt know fusion-icon wasnt in the gutsy repo's sorry, im running hardy.. but we can get it for you

```
sudo gedit /etc/apt/sources.list
```
add this line to the bottom, save and close it
```
deb http://ppa.launchpad.net/maco.m/ubuntu gutsy main restricted universe multiverse
```
```
sudo apt-get update
```
```
sudo apt-get install fusion-icon
```

let me know if that works

---

### Post by SIXAXIS on 2008-04-11
Well, it works, only for that session. As soon as I log out and log back in, it's back to Emerald. I tried closing the program and leaving it open as I log out. Both the same.

---

### Post by joshrobinson on 2008-04-11
did you add fusion-icon to the sessions "startup programs" like i said in my first post?

---

