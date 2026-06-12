---
title: "[SOLVED] Playing Quicktime closes firefox"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-15
I have been trying to play quicktime files from apple.com/trailers.

I have tried playing them using media player connectivity with the default player as, mplayer, gmplayer, and VLC with no luck. It would play the movies in slow motion with pops and clicks of sound.

I have un-installed Media Player Connectivity and changed the default players for all the quicktime file types listed under firefox browser/edit/preferences/manage to both vlc and mplayer. now firefox closes when i try to play quicktime files.

I am pretty sure I have the w32codecs but I tried to install them again anyway and I got this.

```
home@home-desktop:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

---

### Post by Maestro23 on 2007-09-15
Make sure you have your extra repos enabled.  Then try and install them again.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by cwrann on 2007-09-15
Under my software sources I have all of the boxes checked listed under ubuntu software. I have the medibuntu software repository. 

under add remove i have installed "gstreamer extra plugins", "gstreamer ffmpeg video plugin", "xine extra plugins", "gstreamer plugins for mms, wavpack, quicktime, musepack", "GStreamer plugins for aac, xvid, mpeg2, faad"

---

### Post by cwrann on 2007-09-15
problem may be that I have ubuntu 64 I am currently following this post:

[http://ubuntuforums.org/showthread.php?t=54399&highlight=installing+win32+codec](http://ubuntuforums.org/showthread.php?t=54399&highlight=installing+win32+codec)

---

### Post by DjBones on 2007-09-15
could be that there is no AMD64 package for the thing your trying to get,
probably not, but just thought id throw out the idea

---

### Post by cwrann on 2007-09-15
The older thread that I was following ([http://ubuntuforums.org/showthread.p...ng+win32+codec](http://ubuntuforums.org/showthread.p...ng+win32+codec))
didn't wok because the link to the win 32 codec no longer existed. It seems like the rest of the methods could have worked if I had been able to download the codec.

I think that my problem is either a problem with wind32 not being compatible with amd 64 or compiz fusion is screwing it up or both.

---

### Post by cwrann on 2007-09-21
It looks like I had a couple of things going wrong. I got rid of the VLC plugin, I installed gstreamer gl from synaptic and I got rid of media player connectivity. 
I think that Media Player Connectivity was not allowing the computer to buffer the video clips far enough out to make them watchable, and wasn't saving them in temporary files so that I could wait for the entire clip to load before viewing.
Without Media Player Connectivity the browser was shutting down when I tried to play QT, presumably, because I had VLC selected for quicktime files but mplayer set as the prefered overal media player.
or maybe it was all because I didnt have gstreamer gl installed.

---

