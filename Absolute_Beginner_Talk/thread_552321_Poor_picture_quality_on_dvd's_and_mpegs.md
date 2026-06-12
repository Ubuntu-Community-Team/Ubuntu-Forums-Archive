---
title: "Poor picture quality on dvd's and mpegs"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by malayka on 2007-09-16
Hi everyone,

I have just installed Ubuntu Feisty Fawn with my Asus 1680x1050 screen resolution monitor. At first I couldn't use the high screen resolution but managed to solve that with some help, but now when I play a dvd or mpeg video the quality of the picture is poor. Almost as if it is too bright. I have checked the colour depth and that is 24. Has anybody got any ideas what may be causing this? 

Any help appreciated.

Thanks

Chris

---

### Post by st33med on 2007-09-16
What is your video card? To find out, type:
```
lspci
```
And post it here.

---

### Post by malayka on 2007-09-16
Hi

Its an  Intel Corporation 82865G Integrated Graphics Controller (rev 02).

Part of my Dell optiplex sx270........not a great machine admittedly!

chris

---

### Post by Hospadar on 2007-09-16
Are you playing these videos fullscreen?  If the problem is that you are noticing pixelation or artifacts it may be just due to your large resolution.  A regular ntsc dvd is only 720X480 resolution so with your large screen the pixels are going to have to be extrapolated over 4:1 and this might cause some of your problems.  This is sort of just the way things are.  Computer monitors just don't show videos quite the same way as a television.

If the problem is that the video is to choppy or something else, you may need to get the drivers for your video card.

Also, Is this the sort of thing where we could see any of the problems in a screenshot? if so could you send us one?

---

### Post by malayka on 2007-09-17
Hi, 

I'm playing the the dvd's / mpg's in small screens and this doesn't seem to make a difference. 

When I play them on my laptop running XP with a screen res of 1600 x 1200 thay play fine. 

It is as if the brightness has been pushed upto maximum (even though it hasn't)

Pictures appear fine

I couldn't take a pic because the screen shot only shows a blue screen.

Could this be a driver issue?

Thanks

Chris

---

### Post by Butthead on 2007-09-17
You don't have any 3D desktops installed, do you? :confused:

---

### Post by nonewmsgs on 2007-09-17
do all the vidoplayers do this? try vlc and xine and movieplayer and say if there is any difference.

---

### Post by rdfrost on 2007-11-12
I have been having exactly the same problem on a Toshiba Satallite A105-S4284 running (according to fglrxinfo):

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

The problem seems consistent with divx and mpeg files, dvd's, and embedded video on websites; although most of the later are such poor quality it's hard to be sure.

No 3D desktop; running basically a straight-up 7.04 install.

---

### Post by rdfrost on 2007-11-15
Sorry for the delay; internet was down.

VLC seems to correct the problem nicely. Still some issues, but I'll probably start a new thread for those.

Thanks!

---

### Post by malayka on 2008-01-18
Hi,

I have also installed vlc media player and it has improved the quality of the picture massively. 

Thanks for all your help.

Chris

---

