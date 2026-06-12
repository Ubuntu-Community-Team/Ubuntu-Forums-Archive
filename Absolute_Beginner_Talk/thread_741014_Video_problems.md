---
title: "Video problems"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by latanerp on 2008-03-31
I just installed Ubuntu 8.04 on my new laptop (I am running 7.10 on my desktop), but am having two video issues which I have not run into before.

First, when I try to play a DVD in Totem, I get the "Could not read from resource" error but it will let me navigate through the special features using the playlist in the side bar.  I am pretty sure I've installed all necessary codecs, so I am not sure what the issue is.  Has anyone else encountered this? 

Next, when trying to open streaming video in Firefox, it will load the video so that an image appears on the screen--but then the video does not begin to play.  When I right click and open it in Totem, it has information about the video i.e. 28 minute length, but again does not move past the first image (which happens to be, in this case, the logo of the company who made the film).  My desktop computer is still using MediaPlayerConnectivity for streaming video, but when I tried to install it on this computer, it says that it is for an older version of FireFox and does not let me)

Thanks in advance for any assistance.  

p.s. system information: Toshiba Satellite A210 w/AMD Athlon x2 running Hardy Heron for 64-bit

---

### Post by wolfen69 on 2008-03-31
i have found that totem has issues. i remedy this by going into synaptic and completely removing all instances of totem. then:
```
sudo apt-get install mozilla-mplayer vlc
```
i included vlc to replace totem, which is much better anyway.

---

### Post by latanerp on 2008-03-31
DVD: I'm not having much luck with VLC.  When I try to open the DVD, it crashes/closes.

When I try to open DVDs in gxine, the error message is: The xine engine failed to start.  No input plugin was found.  Maybe the file does not exist or cannot be accessed, or there is an error in the URL.  
Or Read error from: Error opening vtsN=-1, domain=2


As for streaming video in Firefox: I just switched VLC to the Preferred Application for Multimedia, and now the video streams but there is no sound.  (Sound is working in Ubuntu generally, I have tested it).

EDIT:  Never underestimate the power of a re-boot.  Rebooted again after installing more codecs in Synaptic and now both problems fixed.  <sigh>

---

