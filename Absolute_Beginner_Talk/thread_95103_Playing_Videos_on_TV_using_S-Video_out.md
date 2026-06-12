---
title: "Playing Videos on TV using S-Video out"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by matthewstory on 2005-11-25
I'm trying to set-up my computer to play only videos out to a TV that i've hooked up to through s-video, i just got a massive external harddrive and i've been saving my movies to it and i'd like to be able to watch them on my tv (btw ubuntu auto detected and auto mounted my new harddrive without even restarting, amazing how far linux has come, i couldn't get SuSe 9.x to detect a USB mouse without restarting).  Anyway, I'm just wondering if i need to install any packages to do this, i've tried just setting the preferences in Totem to do this, but i only have the package to TV-out with DXR3 and everytime i set it to do this it tells me to restart, so i do and then it doesn't work and the preference is reset to no TV-out again after the restart.  Any help on this would be great, thanks.

cheers,
matt

---

### Post by Murgle on 2005-11-30
Are you using totem-gstreamer? thats the default. If so I could recomend using totem-xine because it it supports more formats and work better at least for me.  You will need to install the package w32codecs to play many kinds of files like wmv and some others. It isn't supported by ubuntu and is illegal, but if you want to get it you should look here: [http://ubuntuforums.org/showthread.php?t=94426]("http://ubuntuforums.org/showthread.php?t=94426"). I think that the link in there still works, said too many users when I tried.

---

### Post by el3ktro on 2006-01-29
I'm also searching for a solution for this. It's incredible how much Linux lacks here. All I want is to be able to start a video app (Totem etc.) on my desktop, open a video and click a button so that the video is brought to the TV while I can continue working on the desktop. I have the same issue with Totem and TV-Out, the NVIDIA option is not available :-(

Tom

---

### Post by maxdevis on 2006-01-29
it worked for me with this:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by patrick295767 on 2006-01-29
[QUOTE=el3ktro]I'm also searching for a solution for this. It's incredible how much Linux lacks here. All I want is to be able to start a video app (Totem etc.) on my desktop, open a video and click a button so that the video is brought to the TV while I can continue working on the desktop. I have the same issue with Totem and TV-Out, the NVIDIA option is not available :-(

Tom[/QUOTE]
  
Let us know if you find  tom !
I am also looking to solve this now...

greetz

---

### Post by DDM on 2006-01-31
I'm using breezy and my tv-out is black and white only... This is weird. I finally got around to buying a s-video cable, only to find this. I'll try it out in windows in the meantime, but has anyone else had this issue?

---

### Post by stoffepojken on 2006-01-31
Have you tried this:

[http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv]("http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv")

---

### Post by el3ktro on 2006-01-31
[QUOTE=DDM]I'm using breezy and my tv-out is black and white only... This is weird. I finally got around to buying a s-video cable, only to find this. I'll try it out in windows in the meantime, but has anyone else had this issue?[/QUOTE]

You're most likely just using the wrong video format. Try to play around with PAL-G, PAL-N, NTSC etc.

Tom

---

