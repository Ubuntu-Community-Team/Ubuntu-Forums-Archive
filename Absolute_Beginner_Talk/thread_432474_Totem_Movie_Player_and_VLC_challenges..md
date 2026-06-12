---
title: "Totem Movie Player and VLC challenges."
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by mell0w on 2007-05-04
If anyone can help me id be truly grateful.

For some reason when i play my videos on either mplayer or vlc the vids are messed up.
mplayer has a blue tinge while vlc has a big green bar at the bottom.

---

### Post by teddybairs1 on 2007-05-04
What does it do under Gxine or Kaffeine? It could be a gstreamer problem.

---

### Post by mell0w on 2007-05-04
ill give it a try

EDIT: doesnt seem to play on Kaffeine

---

### Post by mell0w on 2007-05-04
i figured it out....

i removed;

Section "Extensions"
Option "Composite" "Disable"
EndSection

from xorg.conf, unfortunately by doing that the videos seem to drop in frame rate. anyone have a workaround for this?

thank you

---

