---
title: "Help with disply size"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Disposable Arts on 2006-11-22
I got Ubuntu installed and running great, one problem is the display, it dosent take up the whole screen like it should...i dont have a video card...the most i can tell you guys is i have an AOC monitor. Do i need drivers? Any ideas how i can fix this?

---

### Post by ReaderRat on 2006-11-22
Run this in the Terminal (in the Applications>>Accessories menu)....
```
sudo lshw | less
```
and post the output here. This will let us know what kind of hardware you have.

---

### Post by mgmiller on 2006-11-22
You don't say if your monitor is LCD or CRT.  If it is LCD, you should have a button on it somewhere that says "automatic" or some such.  That will tell the display to resize properly.  If your monitor is CRT, you will need to use its own on screen controls to resize the screen and make it fit properly.  This is a common problem with windows as well as Linux.  If the monitor doesn't know the specific combination of refresh rates and resolutions, it won't display full screen, until you go through its own on screen setup to manually adjust the horizontal and vertical width and positions.  It should only take a minute or 2 to do it.

---

### Post by judgejudy on 2006-11-22
> **Disposable Arts said:**
> I got Ubuntu installed and running great, one problem is the display, it dosent take up the whole screen like it should...i dont have a video card...the most i can tell you guys is i have an AOC monitor. Do i need drivers? Any ideas how i can fix this?

try this howto it worked for me :rolleyes: 

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by ReaderRat on 2006-11-24
I found [**THIS**](http://gentoo-wiki.com/Talk:HOWTO_AIGLX#AIGLX_on_savage_video_card)
Hope it may help...

---

