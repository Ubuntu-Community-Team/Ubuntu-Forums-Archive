---
title: "Whats going on here then?"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-02-03
I`ve just placed a dvd in my drive, as per usual, picked one of many dvd players i have, think i chose VLC as it seemed to be the best one. It loaded the disc and promptly exited leavng me with nothing. so i tried totem, same again, then ogle, same again. i dont particularly want to watch it in mplayer as i cannot fill the screen for some reason with the video so does anyone know why my media players might be doing this? Please help i really wanna watch this dvd :cry:

---

### Post by nik on 2006-02-03
Try running the media player from a console to see if you get some helpful output.

---

### Post by Perfect Storm on 2006-02-03
Change the video driver in Mplayer to xv should do the trick.

---

### Post by DiscoKiller on 2006-02-03
this is the output from VLC

mike@xxxxxxxxxxx-xxx:~$ vlc
VLC media player 0.8.4-svn20040920 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: CKY4
libdvdnav: DVD Serial Number: c291c7ca
libdvdnav: DVD Title (Alternative): CKY4
libdvdnav: Unable to find map file '/home/mike/.dvdnav/CKY4.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00004f40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00006173
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000272] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:160000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  0 ()
  Serial number of failed request:  78326
  Current serial number in output stream:  78327

I`m not even gonna try and work out what that means

hope someone can help me

thanks 

DK

---

### Post by DiscoKiller on 2006-02-03
[QUOTE=Artificial Intelligence]Change the video driver in Mplayer to xv should do the trick.[/QUOTE]


that has just made mplayer crash completely.....oh wow....technofear....i cant even get it off my screen

think i`ll send it to workspace 4 and forget about it till it calms down a bit :D

---

### Post by steve.horsley on 2006-02-03
You didn't list xine amongst the viewers you tried. You could always try it.

You should find out about xkill. Run xkill and the cursor turns into a skull and crossbones. The next thing you click will be killed off. Don't try to use the workspace switcher to switch to the right workspace after launching xkill (like I did once) - it'll just kill your switcher.

---

### Post by DiscoKiller on 2006-02-03
th reason i dont have xine is because i have never had any joy with it. yes it worked now and then but it never seemed very useable. same feeling i get with mplayer. i like vlc and ogle because they are simple...press play and select full screen....i like that. i`ll give xine a try and thx for the xkill tip, worked a treat. 

DK

---

### Post by AndyCooll on 2006-02-03
Xine, while maybe not being quite so easy to use is excellent for the fact that it will play just about anything.

I prefer Totem myself, however I have Xine installed just in case Totem doesn't want to play a particular file. I then use Xine and that seems to do the trick. It's worth having it installed just for the Xine engine.

:cool:

---

### Post by DiscoKiller on 2006-02-04
xine seems to play sound but no video, never rated it myself.

---

### Post by jimrz on 2006-02-04
try installing "totem-xine" from Synaptic...naver had any problem getting it to play whatever

---

### Post by DiscoKiller on 2006-02-05
this is the output from ogle when i ran it through terminal. anyone know why this is happening?

mike@XXXXXXXXXX-XXXXXXXXX-XXX:~$ ogle
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshot'
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshotWithSPU'
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00004f40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00006173
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  44
  Current serial number in output stream:  44

---

### Post by DiscoKiller on 2006-02-05
OK after some messing about with my nvidia drivers i`ve solved the problem. thanks for all your help guys

DK

---

