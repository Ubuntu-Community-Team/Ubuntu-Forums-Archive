---
title: "odd error message"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by giggity02 on 2007-11-10
So I'm trying to install guild wars via wine and when I run set up in a terminal i get this:


Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems


no clue what it means, is there something I have to install?:confused:

---

### Post by BoneKracker on 2007-11-10
This probably means you don't have 3d hardware acceleration enabled in your X windows setup.

Typically, one would install binary proprietary graphics card drivers that support 3d acceleration provided by the manufacturer of one's graphics card, indicate those drivers for use in /etc/X11/xorg.conf, and also in that file, load the glx module (which enables X windows to use OpenGL -- which is kind of like DirectX if you're familiar with that).

There is now a point-and-click way of doing this from the system menu, but it has rendered many users computers unusable.  So, you might want to just try that, or you might want to read up a bit first.  I suggest you first make a backup copy of your xorg.conf file, then give the point-and-click method a shot.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

There are lots of posts in here as well as information in the documentation (wiki, etc.) about 3d accleration, nvidia drivers, ati drivers, glx, dri, etc.

[edit]: If you've already got glx working fine, but it's just not working with your wine, then what I'm suggesting above is irrelevant.

---

### Post by giggity02 on 2007-11-10
I don't think its that because it did this before and i was able to type some code in and get it to work fine but i forgot what i did lol :(

---

### Post by giggity02 on 2007-11-10
:(

---

### Post by atomkarinca on 2007-11-10
[here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194")'s a guide for how to get the game running.

i suggest you to also bookmark this page, it's very handy.

---

### Post by giggity02 on 2007-11-10
> **atomkarinca said:**
> [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194")'s a guide for how to get the game running.

i suggest you to also bookmark this page, it's very handy.

if this works.. I LOVE YOU :lolflag:

---

### Post by giggity02 on 2007-11-10
still get that message once I type in gwsetup.exe :(

---

### Post by giggity02 on 2007-11-10
anyway i'm going to sleep.. keep helping me out people you know you wanna :)

---

### Post by giggity02 on 2007-11-10
golly gee friggen willikers, now ubuntu won't stop loading in low graphics mode ='[ WTF..... i could live with this if only guild wars worked ='[

---

### Post by shad0w_walker on 2007-11-10
It definitely sounds like a graphics driver problem. Your best bet is to try reinstalling them.

---

