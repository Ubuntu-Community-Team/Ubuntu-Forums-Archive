---
title: "Issues playing video on Intel 915 Integrated"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by johnnyloot on 2007-05-12
Hello All,

Just did a fresh install of Fiesty on my Dell Inspiron E1405 which has an Integrated Intel Video Card. 
I got automatix and installed all the Non-free codecs as well as VLC. The issue is that when I try to play video in Totem, the movie screen is covered in small blue dots in a grid. Cant seem to get rid of them, so I figure hey, VLC should work, but no dice. VLC gets sound but no video. 

Are there some codecs im missing? I can try other players, but it seems like an issue on my end. Any help would be appreciated.

---

### Post by deadgobby on 2007-05-12
What type of video format are you trying to play?

---

### Post by johnnyloot on 2007-05-12
Sorry,
im trying to play an AVI movie.

Just as an aside, I have installed the w32codec and libdvdcss codecs as well. Same issue.

---

### Post by johnnyloot on 2007-05-12
disable desktop-effects and all works! Totem, VLC. 

Any help on why desktop effects would cause this problem?
Or soultions?

---

### Post by ramjet_1953 on 2007-05-12
Have you tried installing the intel video driver?

If not, copy and paste this into a terminal window:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

Re-boot and see if this helps.

btw, this seems to work better than the [COLOR="Blue"]915resolution[/COLOR] package and is fully automatic.

Regards,
Roger 8)

---

### Post by johnnyloot on 2007-05-12
no luck.

Install went well, but when i enable desktop effects, the workspaces just fade to the next one, no cube. Totem now fails to even open the video.

---

