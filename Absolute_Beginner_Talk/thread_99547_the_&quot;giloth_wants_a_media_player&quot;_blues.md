---
title: "the &quot;giloth wants a media player&quot; blues"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by giloth on 2005-12-05
I'm trying to get off the Windows bandwagon and get that apps I need for Ubuntu. I was hoping someone could help point me in the right direction of a media player.

I'm wanting one similar to Windows Media Player or MusicMatch where you can have a Library of files. It'd also be nice to be able to have them play embedded files within Firefox.

What are your suggestions?

---

### Post by cilynx on 2005-12-05
Rhythmbox is probably what you're looking for.

---

### Post by giloth on 2005-12-05
I have been trying it a little (with the default install of Ubuntu 5.10) but when trying to add my music it says that it can't add it because it's not an audio stream.

Also, does this program support video files or only music?

---

### Post by CPUFreak91 on 2005-12-05
RealPlayer?
I like xmms and RealPlayer for all my streaming and music and I use VLC and Xine for DVD

---

### Post by CPUFreak91 on 2005-12-05
[QUOTE=giloth]I have been trying it a little (with the default install of Ubuntu 5.10) but when trying to add my music it says that it can't add it because it's not an audio stream.

Also, does this program support video files or only music?[/QUOTE]

First off, click on the GNOME help (life saver icon) it provided me with the answer to the same question and many more. Or go to the ubuntu wiki: [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

Second, type this:

apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg 

all of it. And it should work for you.
For DVD's (Encrypted) go here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by AndyCooll on 2005-12-05
Amarok is good for audio file lists etc (unfortunately it doesn't do video though)

:cool:

---

### Post by CPUFreak91 on 2005-12-05
oh, also when your finished, type: gst-register-0.8

---

### Post by cilynx on 2005-12-05
Due to copyright issues, Ubuntu doesn't include mp3 support by default.  To get it, you need to enable the Universe repository and

apt-get install gstreamer0.8-mad

Once you've done that, Rhythmbox will play/sort/whatever mp3's

---

### Post by kalos on 2005-12-05
[QUOTE=giloth]when trying to add my music it says that it can't add it because it's not an audio stream.[/QUOTE]

What kind of audio files are you using? If you don't have the codecs, then you can't play them. You should try running [Automatix](http://ubuntuforums.org/showthread.php?t=80295) to install multimedia codecs. You can do this other ways, but I can't recall the apt-get method, but it might be just ```
sudo apt-get w32codecs
```. Anyway, Automatix makes installing a bunch of basic stuff really easy.

[QUOTE=giloth]Also, does this program support video files or only music?[/QUOTE]

Rhythmbox doesn't, but you might want to try Totem or Xine. I believe Totem is installed by default. Note that if you want to play many videos, you will probably have to install some codecs (again). Automatix will do this for you too.

-kalos

---

### Post by giloth on 2005-12-05
Thank you everyone for your help! I have everything up and running. amarok seems like the media player that I'll be sticking with, but I only wish that videos could be played under it as well. Oh well, I'm happy. Totem's plugin in firefox doesn't seem to work very well I've found.

I'll figure it out though. Thanks again! :D

---

### Post by kalos on 2005-12-05
Try the mplayer plugin ```
sudo apt-get update
sudo apt-get install mozilla-mplayer
```

edit: forgot to update apt-get
edit: forgot to install. doh!

---

### Post by giloth on 2005-12-06
Yeah I've tried that before as well as a couple others, but everyone I've tried seems too unstable.

---

### Post by CPUFreak91 on 2005-12-06
[QUOTE=giloth]Totem's plugin in firefox doesn't seem to work very well I've found.[/QUOTE]

You could try the mplayer mozilla plugin

nvm someone already said that before I had a chance to finish this.

---

### Post by giloth on 2005-12-06
Just for other new beginners on this subject, I've found that the VLC plugin for Firefox seems to work the best. :)

---

### Post by Gray. on 2005-12-06
What I personally use is totem-xine (got it using Automatix) and then got the Firefox extension MediaPlayerConnectivity. This way it opens embedded files with ease. You might want to give it a try.

---

### Post by giloth on 2005-12-08
Bah, I've tried that extension. Never really liked it all that much. Thanks for the suggestion though. :)

---

