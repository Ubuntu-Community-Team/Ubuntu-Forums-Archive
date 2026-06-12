---
title: "Ubuntu / App Annoyances"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by pbwalker on 2006-08-24
I recently switched over to Ubuntu from Fedora. I am loving it so far...but I had some questions...slight annoyances. I searched but found nothing.

1. Do I HAVE to use a mozilla plugin for videos? I would like for it to open VLC or Movie Player / mPlayer. I don't want it to open up in Firefox.

2. It is very annoying when I am watching a video...and I want to open a new video, I can't just double click the video. It opens a new session of VLC or mPlayer (in addition to the existing session that is already open). Is there a way to get it to use the existing session?

3. I installed fglrx-control for my ATI Radeon Express 200M. Where the heck is it? :)

4. I've got my BCM 4318 Air Force 54g card working great...only at work. It's weird. I have my router in mixed mode...it worked one night...and hen it never worked again. Can anyone point me in the direction of a place to look?

-Brian

---

### Post by calvinthomas on 2006-08-24
I'm sorry I can't help with the first couple although i'm sure a fix is possible and probably quite simple!

For number 3: Go to a run applications prompt (or the terminal) by pressing ALT F2 and type:

fireglcontrolpanel

For number 4: [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

HTH

Calv

---

### Post by nanotube on 2006-08-24
> **pbwalker said:**
> I recently switched over to Ubuntu from Fedora. I am loving it so far...but I had some questions...slight annoyances. I searched but found nothing.

1. Do I HAVE to use a mozilla plugin for videos? I would like for it to open VLC or Movie Player / mPlayer. I don't want it to open up in Firefox.


in firefox, go to edit>preferences>downloads, click the "view and edit actions" button, and edit the actions for whatever filetypes you want (ie, set the movie filetypes to open with an app, rather than with the plugin).

> 
2. It is very annoying when I am watching a video...and I want to open a new video, I can't just double click the video. It opens a new session of VLC or mPlayer (in addition to the existing session that is already open). Is there a way to get it to use the existing session?


well, from "man gmplayer", the following options may be of use:

```
-enqueue (GUI only)
              Enqueue files given on the command line in the playlist instead of playing them
              immediately.

       -fixed-vo (BETA CODE!)
              Enforces  a  fixed  video system for multiple files (one (un)initialization for
              all files).  Therefore only one window will be opened for all files.  Currently
              the  following  drivers  are fixed-vo compliant: gl, gl2, mga, svga, x11, xmga,
              xv, xvidix and dfbmga.

```

so, just put these prefs into your ~/.mplayer/config file

for vlc, i haven't been able to find anything like that...

> 
3. I installed fglrx-control for my ATI Radeon Express 200M. Where the heck is it? :)



/usr/bin/fireglcontrolpanel
you can run it from the terminal, set a shortcut to it, or use the alt-f2 shortcut as suggested above.

---

