---
title: "mplayer plugin"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by mars2010 on 2007-12-06
I am using Ubuntu 7.10 - o Gutsy Gibbon and access internet through Firefox 2.0.0.11. showed I installed mplayer and mplayer plugin for mozzila. I checked in the terminal and it showed that is already installed but the videos cannot run. If somebody can help me I will be very thankfull,

---

### Post by frank002 on 2007-12-06
You need to install the codecs. Open Synaptic and search for gstreamer. Download the gstreamer good, gstreamer ugly, gstreamer bad, gstreamer ffmpeg, and the fluendo mp3. I may have left some out but I am sure someone else here can tell you if you need any more. Good Luck.

---

### Post by mars2010 on 2007-12-07
I am gonna try thanks for answering me

---

### Post by marmaladejackson on 2007-12-07
I'm having a similar problem... Last week, .mov and .dvix streams stopped working (see attached pic), which prompted me me to re-install firefox (see my other post about all the problems I had re-installing firefox32 on the 64bit platform).  With help, I got firefox32 up and running again, but .mov and .divx streams still don't work.  I can't think of any changes I've made that would cause that to happen.  Any suggestions?

Thanks!

---

### Post by marmaladejackson on 2007-12-07
OK, this worked for me:

Using synaptic I installed the VLC plugins, gstreamer plugins, and quicktime plugins.  Restarted firefox and it worked.

---

### Post by Chelidon on 2007-12-08
I don't know how related this is but every time I try to stream video firefox just shuts down completely. I know I can stream audio (with a little difficulty), but the video will load to a point and then not play or crash firefox. I do have mplayer. I have VLC also but not the plugin.

okay, after taking a gander at my package manager it appears I don't have any gstreamer packages installed. It would probably help if I had some of it, no? Hehe

Currently installing the gstreamer plugins Frank suggested.

Excellent. It works!

---

### Post by mars2010 on 2007-12-08
I a gonna try VLC plugins. Thanks a lot

---

### Post by ImALittleTeaPot on 2007-12-12
I've tried both of those. Divx still won't work for me....but it used to work.  Mplayer used to play divx video streamed in from tv sites like [www.surfthechannel.com](www.surfthechannel.com), But the quality was horrible. So....I uninstalled it from synaptic, installed vlc and its mozilla plugin, and that didn't even play the vids on surfthechannel at all. So.....i tried to return to mplayer, but when I reinstalled it, no divx plugin. Opened up a browser....typed in about:plugins and every plugin that was previously installed returned, except 2 divx plugins.

---

### Post by fliptomato on 2007-12-14
Hello everyone -- I'm also a beginner who has only recently been having problems with Mplayer. Last week Mplayer was working just fine, but a day or two ago it seems to have stopped working with divx streams (from stage6.com for example). 

I am using Ubuntu Dapper, and used the mplayer installation here:
[http://ubuntuforums.org/showthread.php?t=540412&highlight=divx+mplayer+mozilla](http://ubuntuforums.org/showthread.php?t=540412&highlight=divx+mplayer+mozilla)

I checked my /usr/lib/mozilla-firefox/plugins folder, and my file browser has a red 'x' on the following files:

mplayer-in-dvx.so
mplayerplug-in-dvx.so
mplayerplug-in-dvx.xpt

Double-clicking gives the notice: "The link ___ is broken. Move it to wastebasket?"

Is there a way to fix this?
Thanks,
F

---

### Post by breaking on 2008-01-27
it worked fine for me with TV Shack, [http://www.tvshack.net](http://www.tvshack.net)

---

