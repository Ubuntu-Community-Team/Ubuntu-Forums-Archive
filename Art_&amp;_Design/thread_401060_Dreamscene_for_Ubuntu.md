---
title: "Dreamscene for Ubuntu??"
date: 2007-04-04
forum: Art &amp; Design
---

### Post by MadsRH on 2007-04-04
Can I get somthing like Vista's Dreamscene for Ubuntu? Perhaps included in Compiz, Beryl or Looking glass?

[http://windowsultimate.com/blogs/extras/archive/2007/01/07/windows-dreamscene.aspx](http://windowsultimate.com/blogs/extras/archive/2007/01/07/windows-dreamscene.aspx)

**MadsRH**

---

### Post by Pucce on 2007-04-04
You should try xwinwrap.

---

### Post by rabid9797 on 2007-04-04
frontend for xwinwrap w/ beryl
[http://forum.beryl-project.org/viewtopic.php?t=3488](http://forum.beryl-project.org/viewtopic.php?t=3488)

---

### Post by LinuxIsInnovation on 2007-12-09
Please provide something for compiz.. Im using Gutsy.

---

### Post by smartboyathome on 2007-12-09
It will work with Gutsy too (Compiz Fusion in Gutsy is just Beryl+Compiz core).

---

### Post by LinuxIsInnovation on 2007-12-09
The link provided for the frontend doesnt have any download link.. 
And I had installed xwinwrap package.. no launcher was created, neither did it install some command line tool..
Please guide me how do I install xwinwrap and get along with DreamScene.. Im new in the Ubuntu family you see :)

---

### Post by smartboyathome on 2007-12-09
Have you tried my howto?
[http://ubuntuforums.org/showthread.php?t=577144](http://ubuntuforums.org/showthread.php?t=577144)

---

### Post by LinuxIsInnovation on 2007-12-10
This isnt working..When I start the movie, the desktop turns into a bluish shade.. I can hear the audio but the video isnt played.. Ive done exactly as you said in the previous steps. I am using X11 output for MPlayer..

---

### Post by smartboyathome on 2007-12-10
Do you get any output from the terminal for xwinwrap?

---

### Post by LinuxIsInnovation on 2007-12-10
Heres the output I get:
root@glade-laptop:/home/glade# xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet Raindrops.mpg
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Raindrops.mpg.
MPEG-ES file format detected.
VIDEO:  MPEG2  1280x720  (aspect 3)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 1280 x 720 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 

gnome_screensaver_control()
Exiting... (End of file)
mplayer died, exit status 0
root@glade-laptop:/home/glade# 

And heres a screenshot of what I see:
[http://i9.tinypic.com/80pfcdt.png](http://i9.tinypic.com/80pfcdt.png)

---

### Post by LinuxIsInnovation on 2007-12-10
My desktop is gone
When I removed the wallpaper from compiz settings, I got a black desktop with no icons on it
I also did this:
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true && nautilus

This command starts the gnome-mount extension and the Gutsy default wallpaper appears. But still, there are no icons and when I right click on the desktop, no menu appears..
I also enabled the Show Desktop option under Nautilus preferences in gconf editor.. but it didnt help either.

---

### Post by LinuxIsInnovation on 2007-12-10
Anyway, my desktop came back.. please help me with dreamscene though..

---

### Post by angryforumreader on 2008-04-03
Im fed up with people offering vlc as an alternative to dreamscape. What people (like me) wanted was someway to play those *.dream files as our desktop background.

VLC yes it can play movies in the background but so far has anyone gotten hold of any application to convert dream to movies? no. Whats up with the dream files anyway? Why only vista can operate it? If not why is there no activity to code a program that works on dream files.

---

### Post by NightwishFan on 2008-04-03
Because Microsoft made it. I for one, would rather not have a video wallpaper eating up cpu. Also I believe there is one third party app to do something like that although you have to pay for it (of course). It is the people that made all the Xp themers and such.

---

### Post by shafin on 2008-04-04
> **angryforumreader said:**
> Im fed up with people offering vlc as an alternative to dreamscape. What people (like me) wanted was someway to play those *.dream files as our desktop background.

VLC yes it can play movies in the background but so far has anyone gotten hold of any application to convert dream to movies? no. Whats up with the dream files anyway? Why only vista can operate it? If not why is there no activity to code a program that works on dream files.
These dream files can be made into movies,actually,playing .dream files require dreamscenes and Stardock deskscape (original dreamscene can only play movie files,not .dream files,they are functionality added by deskscape).

When a dream file is loaded as background,it's decompressed and the original file in the movie format can then be fetched from deskscapes' cache, I've recovered some of my favourite backgrounds in that way. Then you can use them on vlc.

---

