---
title: "Video Problem: Fine, Horizontal Lines + Tiny Dots"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by Hesse on 2005-12-31
Installed Ubuntu 5.10 on a Toshiba Satellite laptop with GeForce FX Go 5600 video card; am having video troubles.

When playing any type of video file (.avi, .mpg, .ogg, etc.) on any player (Mplayer, VLC, et al), dozens of very thin "lines" run across the video screen and lots of tiny, blue-ish dots flicker on the left side of the screen. When the player is windowed, these are not a problem; however, when I switch to "full screen" mode, or stretch the window to fill more than 3/4 of my screen, they appear and annoy. When I pause the video file, the lines (and dots) remain and flicker.

I've downloaded the Nvidia drivers via Synaptic, tried different resolutions, and searched the forum, but I can't find a solution.

Any ideas? 

Thanks.

---

### Post by prizrak on 2005-12-31
As a Toshiba user myself, they seem to have some really weird video (general hardware) problems for no reason. My only guess is that the video card is somehow not standard, maybe try googling to see if other Linux distros have the same problem. Also you might wanna try grabbing the w32codecs from the web if you haven't yet, and maybe try a different Desktop Environment (KDE, XFCE) maybe Gnome just doesn't like you for some reason.

---

### Post by eriqk on 2006-01-01
I suspect you're looking at interlaced video, and your player doesn't de-interlace on the fly. The fine lines you're seeing are scanlines that make up the images. First the odd ones, then the even ones. You'll notice them during fast motion.

Groet, Erik

---

### Post by poofyhairguy on 2006-01-01
Use Gxine and turn up the post-processing in the menu. Master of Universe is your friend.

---

