---
title: "trouble with avi files, I thought I installed all the codecs!"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by abben on 2007-05-14
trying to get an AVI file to play but so far it is not working.

What I have done:

I've installed libdvdcss2 and w32codecs
I've installed VLC and mplayer, in addition to totem.
I've installed the "GStreamer ffmpeg video plugin", "GStreamer extra plugins", "GStreamer plugins for aac, xvid, mpeg2, faad", "GStreamer plugins for mms, wavpack, quicktime, musepack"
I've added Mediabuntu to my list of repositories, and it is fully updated.

Is there *anything* else I could do/install to add missing functionality for any certain kind of video files?

Lastly, these are the responses I get from the various video players when attempting to play the avi file...

Totem - "An error occurred. Could not determine type of stream."
mplayer - "Error opening/initializing the selected video_out (-vo) device."
VLC - acts as though it is playing something, displaying no sound or video for about 5 seconds, then ends.

Any help is greatly appreciated.

---

### Post by forestpixie on 2007-05-14
Hi I got media player going by following this thread 

[http://ubuntuforums.org/showthread.php?t=400039&highlight=error+opening+selected+video+out](http://ubuntuforums.org/showthread.php?t=400039&highlight=error+opening+selected+video+out)

3rd post johhny4north

i've also got a lot of codecs from synaptic which i imagine you've already done - one had ugly in the tex i believe

i'll have another look

---

### Post by forestpixie on 2007-05-14
from add/remove showing any application i have

gstreamer extra
gstreamer ffmpeg video
xine extra plugins
gstreamer for aac xvid 
gstreamer for mms wav pack

good luck

---

### Post by forestpixie on 2007-05-14
sorry - found the other ones i have in synaptic now 
libxine1-ffmpeg
libzine-extracodecs
w32codecs

I have no problem (speak too soon) playing anything audio or video with the codecs i have

---

### Post by Roger Gundberg on 2007-05-14
You might want to download 'Automatrix'. Check it out!

---

### Post by silent1643 on 2007-05-14
[easy ubuntu]("http://easyubuntu.freecontrib.org/overview.html") installs most multimedia codecs as well

---

