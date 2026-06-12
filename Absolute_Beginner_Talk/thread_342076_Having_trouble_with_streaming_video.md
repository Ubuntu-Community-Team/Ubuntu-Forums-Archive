---
title: "Having trouble with streaming video"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by jonbue on 2007-01-19
i just switched from fedora core to ubuntu and im having problems getting video to work in firefox i tried to install totem-xine but for some reason ubuntu keeps removing it and reinstalling totem-gstreamer.my question is how can i get firefox to play streaming formats like rm and wmv files i tried mplayerplug-in but for some reason it comes up with a grey box like firefox isnt picking up the plugin. any help on this would be so appreciated :)

---

### Post by jonbue on 2007-01-19
ok i found out its the totem-mozilla plugin which i removed it also removed this ubuntu-desktop file is that necessary or can i ignore it?

---

### Post by shareMenaPeace on 2007-01-19
I used getautomatix.com, a tool for application install to install a ff media plugin.

---

### Post by Verbatim9 on 2007-01-19
I believe ubuntu-desktop is a pseudopackage (that is, there's no software related to it specifically, it's just an empty package with a bunch of dependancies, so that you get everything you need to use the default ubuntu/gnome desktop when you install it). However, if the *only* extra thing that was uninstalled was ubuntu-desktop, you didn't actually uninstall anything except the plugin.

As for what you need to do to get the plugins you need...I'm afraid I haven't a clue...installing automatix is probably the easiest solution (it's designed to help install all kinds of non-free junk easily).

---

### Post by r4ik on 2007-01-19
> **jonbue said:**
> i just switched from fedora core to ubuntu and im having problems getting video to work in firefox i tried to install totem-xine but for some reason ubuntu keeps removing it and reinstalling totem-gstreamer.my question is how can i get firefox to play streaming formats like rm and wmv files i tried mplayerplug-in but for some reason it comes up with a grey box like firefox isnt picking up the plugin. any help on this would be so appreciated :)

Right click the box

set 'video" to x11
and "sound" to alsa

Should work.

Good luck !

---

### Post by jonbue on 2007-01-19
thanks guys worked like a charm :)

---

### Post by keith11 on 2007-01-23
Hi, I have the same problem and I am typing here after going through all the guides and wikis there are out there for playing streaming video on linux. I have not been able to play online video whether it's real or windows media. I have the win32codecs, totem-xine, mozilla-mplayer and all the other packages installed that are mentioned on the Restricted Media format guide in this forum. Whenever I try to play an online video, either in Firefox or Mozilla, there appears nothing on the video screen. In Firefox, the screen just stays gray and the message on the bottom shows "done", but no streaming occurs. In Mozilla, the screen of the video playback at least shows that I need a plugin. Following are the contents of:

1. /usr/lib/mozilla/plugins

libnullplugin.so                 mplayerplug-in-dvx.so
libtotem-basic-plugin.so         mplayerplug-in-dvx.xpt
libtotem-basic-plugin.xpt        mplayerplug-in-qt.so
libtotem-complex-plugin.so       mplayerplug-in-qt.xpt
libtotem-complex-plugin.xpt      mplayerplug-in-rm.so
libtotem-gmp-plugin.so           mplayerplug-in-rm.xpt
libtotem-gmp-plugin.xpt          mplayerplug-in.so
libtotem-mully-plugin.so         mplayerplug-in-wmp.so
libtotem-mully-plugin.xpt        mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.so   mplayerplug-in.xpt
libtotem-narrowspace-plugin.xpt

2. /usr/lib/mozilla-firefox/plugins

libtotem-basic-plugin.so         mplayerplug-in-gmp.so
libtotem-basic-plugin.xpt        mplayerplug-in-gmp.xpt
libtotem-complex-plugin.so       mplayerplug-in-qt.so
libtotem-complex-plugin.xpt      mplayerplug-in-qt.xpt
libtotem-gmp-plugin.so           mplayerplug-in-rm.so
libtotem-gmp-plugin.xpt          mplayerplug-in-rm.xpt
libtotem-mully-plugin.so         mplayerplug-in.so
libtotem-mully-plugin.xpt        mplayerplug-in-wmp.so
libtotem-narrowspace-plugin.so   mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.xpt  mplayerplug-in.xpt
libunixprintplugin.so

I had Mandriva Powerpack 2007 installed earlier but I had the same problem in there too. I am not sure what I need to make this work. I just noticed I am not able to play any video file in Mplayer as a stand alone player too. The error I get while trying to play a video file in Mplayer is "Error opening/initializing the selected video _out (-vo) device". When I try to play an MP3 file it gives an error saying "Requested audio codec family [mp3] (afm=mp3lib) not available. Enable it at compilation." But it still plays the audio file with not so clear quality. Any suggestions please?

I am attaching the screenshot of the error I get in Mozilla as well as in Firefox.

---

