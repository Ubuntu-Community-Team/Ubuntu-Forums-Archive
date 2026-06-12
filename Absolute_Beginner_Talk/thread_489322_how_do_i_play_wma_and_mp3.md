---
title: "how do i play wma and mp3"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by TrevorRS on 2007-07-01
right i have limewire and i have downloaded a load of files but how do i play themj without loading up limewire?

looking to play wma and mp3 files!

Cheers
Trevor

---

### Post by Princey on 2007-07-01
Have you tried doubleclicking/opening any of the music files? You'll get a prompt if the necessary codecs aren't installed and telling what to do next.

---

### Post by Jimmyfj on 2007-07-01
you could install Amarok or XMMS on your system

---

### Post by Grigorius on 2007-07-01
Download VLC ... (add/remove) and have a look here:

[https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

or better yet get thru this:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

EDIT: to play Mp3 files you can use Rhythmbox which ia already installed see applications/video&music/Rhythmbox

---

### Post by heatpumpcontrol on 2007-11-03
> **TrevorRS said:**
> right i have limewire and i have downloaded a load of files but how do i play themj without loading up limewire?

looking to play wma and mp3 files!

Cheers
Trevor

Well you can use Rhythmbox. However, you have to install the gstreamer 10 bad, bad-multiverse, ugly and ugly-multiverse plugins and if that doesn't work then make sure the following are installed:

gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-gl
gstreamer0.10-gnomevfs
gstreamer0.10-pitfdll
lgstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-dbg
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-bad-multiverse-dbg
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-base-dbg
gstreamer0.10-plugins-farsight
gstreamer0.10-plugins-good
gstreamer0.10-plugins-good-dbg
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-dbg
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-ugly-multiverse-dbg
gstreamer0.10-gstreamer0.10-schroedinger
gstreamer0.10-sdl
gstreamer0.10-tools
gstreamer0.10-x
gstreamer-dbus-media-service
gstreamer-tools
libgstreamer0.10-0
libgstreamer-plugins-base0.10-0
libgstreamer-plugins-pulse0.10-0
totem-gstreamer
ubuntu-restricted-ng-gstreamer

**[COLOR="Red"]NOTE[/COLOR]**: These are the ones that I have installed in my system. I'm not an expert but I wanted to help out someone with the same issue. I really like Rhythmbox as it's similar to iTunes in my opinion. 

After went through and ensured that everything gstreamer was installed, my Rhythmbox played my wav files.

Good luck

[COLOR="DarkOrange"]**Update**[/COLOR]

On my home pc I noticed that the above still didn't work though it worked on my work pc and my laptop. I read some more and performed other suggestions:

Reinstall 
MPlayer
Gxine

this can be done from the add/remove

My home pc now plays wmas. Weird but at first the pc would play wma using MPlayer but later on I noticed it didn't. After reinstalling the above apps, everything now works. Finally.... 3 days and maybe about 8hrs later. (yes I know, I have no life. lol)

---

### Post by FuturePilot on 2007-11-03
This is a great link for multimedia codecs and stuff
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Rabindranath on 2007-11-03
Try checking the gstreamer plugins in synaptic. Or click yes when a player asks you whether to download the necessary codecs when you  try to open a mp3 or wma file. Or install vlc through synaptic. It plays every filetype i know. If you dont have internet connection in ubuntu, go to 
[http://ubuntuforums.org/showthread.php?t=589274](http://ubuntuforums.org/showthread.php?t=589274)

---

### Post by Frak on 2007-11-03
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by Billy_McBong on 2007-11-03
[COLOR="blue"]the peoples seem to have answered your question but i would suggest using frostwire instead of limewire. its pretty much the same just faster and doesn't have the ad telling you to get pro[/COLOR]

---

### Post by Frak on 2007-11-03
> **Billy_McBong said:**
> [COLOR="blue"]the peoples seem to have answered your question but i would suggest using frostwire instead of limewire. its pretty much the same just faster and doesn't have the ad telling you to get pro[/COLOR]
I agree, and they have an Ubuntu native installer.

---

### Post by AndyCooll on 2007-11-03
> **Frak said:**
> ```
sudo aptitude install ubuntu-restricted-extras
```

That would work ...however doesn't that also install a load of other stuff not related to codecs?

:cool:

---

### Post by Frak on 2007-11-03
> **AndyCooll said:**
> That would work ...however doesn't that also install a load of other stuff not related to codecs?

:cool:
Fonts, Flash, Java, and Codecs.

---

### Post by heatpumpcontrol on 2007-11-05
> **Frak said:**
> ```
sudo aptitude install ubuntu-restricted-extras
```

This worked too. Probably a better choice or option.

---

