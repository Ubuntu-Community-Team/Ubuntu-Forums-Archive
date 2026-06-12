---
title: "so i really like the new desktop effects. but."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-04-22
im having a mild problem.

any 3d effects, or videos playing dont work.

im using an ati 9200 with the open source drivers. 

im sure there's gotta be some settings i can add to my xorg file to enable both the 3d and the videos to work with the desktop effects on.  anyone have any suggestions?

---

### Post by mills on 2007-04-22
i have the same card and i had to install errmmm desktop manager or gl manager from synaptic to get it workin properly

you'll have to forgive my vagueness, iam currently in windows so cant check exactly what its called

---

### Post by mills on 2007-04-22
sudo aptitude install gnome-desktop-manager

then it will be in preferences -> gldesktop

**EDIT**: sorry its sudo aptitude install gnome-compiz-manager

---

### Post by richaoj on 2007-04-22
you have to change the settings for gstreamer

in terminal

gstreamer-properties

on the video tab select:
X-Window System (no xv)

should fix the problem . . .

---

### Post by graigsmith on 2007-04-23
awesome :)  thanks guys.

---

### Post by graigsmith on 2007-04-23
k, so now the video works, but the 3d in a window game played thru wine doesn't work properly.

it stays on top of the ui,  but you cant see the window. and when you rotate the cube. it doesnt rotate. it just stays on the flat area where it was.   Is there some way to fix this ?

---

### Post by SZ07 on 2007-04-24
I'm having the same problem. When a game is playing and the cube is rotated, the game screen doesn't move with its window. Also, when I just normally move the game window, I get the exact same result. Any help would greatly be appreciated.

---

### Post by SZ07 on 2007-04-24
OK, I don't know how much help this will be but I'll describe a few things that I tested out. When I disabled OpenGL rendering in my games, the game screen would no longer stick (i.e. it behaved normally like other windows) when the cube was rotated. This seems to be one way to solve this problem.

However, the problem with this is that when Beryl (or Compiz) is enabled and OpenGL rendering in the games is disabled, the games' performance takes a big hit, as evidenced by a big drop in the frame rate. To get decent performance while Beryl is running, OpenGL rendering in the games has to be enabled, but then this leads to those "sticky" game screens.

Not sure if there is any work around for this.

---

### Post by graigsmith on 2007-04-24
probably just need to get a better videocard. though i really like not having to install any drivers for this ati 9200.

---

