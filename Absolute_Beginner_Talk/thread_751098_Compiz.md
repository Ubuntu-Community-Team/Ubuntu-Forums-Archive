---
title: "Compiz"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by susanpenter on 2008-04-10
After having used Kubuntu for a while after moving from Windows I am now using Ubuntu and so far like what I see.  I have installed Compiz but I seem to be able to get some things to work and not others.  For instance I can scroll my wheel and the four desktops rotate in a cube but I can't get the cube to become 3D with a Skydome background, the wobbly windows is working but the water and fire are not, they say disabled in the options.

I have dream image of what I would like to see eventually:

A rounded cube with a live image world map as the background, when you go to a part of the world in sunlight the skydome is lit with a light cloudy sky, when you go to a part of the world where it is night time the skydome is a starry sky.

I appreciate that this will take a long time (if ever) to achieve but I would like to begin by at least having a 3D cube.  Can anyone advise me, in order, of which packages I might need and where I can find manuals for them.

Many thanks
Susan

---

### Post by jolx on 2008-04-10
hav u installed advanced desktop effects settings?

---

### Post by sayakb on 2008-04-10
All you need is ccsm:```
sudo apt-get install compizconfig-settings-manager
```Open ccsm and enable "Paint fire on desktop". Now hold down Win key + Shift + Mouse Button 1 to draw fire. ress Shift+Win+C to clear. Plus, get a big world map image. Enable desktop cube, rotate cube, cube caps. Goto Rotate cube and set the Zoom level to 0.4000. Goto Desktop Cube abd add the world map as the skydome image. Enable the Skydome checkbox and also the Animate skydome checkbox.
You might not have water waves but you may have rain effects.

---

### Post by CJ56 on 2008-04-10
Try this tutorial - it may not get everything you want but I found it very useful for getting the cube up & spinning....

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

Hope it helps - ;)

---

### Post by susanpenter on 2008-04-10
I tried following your advice but this is how things look in the manager screen.

---

### Post by susanpenter on 2008-04-10
I now have a situation where if I press Cont and Alt and hold the down button I am shown four screens with a mirrored gray screen below and a black screen above.  As soon as I let go of Cont and Alt it snaps back to the current screen.  

This is fine but I told it to make a cube rather than give me a row of windows, also I would like to be able to let go and have the effect stay there until I told it to refocus on one window.

Cheers

---

### Post by CJ56 on 2008-04-10
Well the way it works on mine is to 

- Go to Advanced Desktop Settings
- Go to General Options
- Desktop Size tab & change Horizontal virtual size to 4, leaving the other settings at 1
- Then tick Zoom Desktop, Desktop Cube, Rotate Cube, Cube Reflection & Cube Caps

I think after all that if you hold down Ctrl + Alt and point the cursor at an empty bit of the desktop you can flip the cube around & rotate it & whatnot

But as I say, check Forlong's blog. It has most of the answers

Incidentally, once you want to turn off the cube, untick the functions in the reverse order to that in which you ticked them... I managed to freak out Compiz quite badly once by doing it from the top down...

Also have you tried the Expo function? That'll give you 4 walls in one view...

---

### Post by susanpenter on 2008-04-10
I'm getting there thanks, I have the Cube:) I also have a nice starry sky in the skydome.  The next bit to work out is how to have a world map spread around all the sides of the cube, the blog has been pretty helpful but it gives quite a bit in code, I am safer using menus and selecting options.  For some reason although I have the extra plugins installed several options like the water and fire writing are still saying disabled even after I have enabled them.

---

