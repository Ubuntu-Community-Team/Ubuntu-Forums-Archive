---
title: "Issue with video in browser"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-11-08
Some weird things going on with video:

It seems that certain types of videos won't play for me. I can get flash stuff to work fine (youtube and google video are working for me), but with many other types, I get a rectangular bar-shaped thing inside the video screen. There is video, sorta; it's as if the picture has been compressed into this rectangle.

The same thing happens in any video player program other than VLC.

Any ideas?

---

### Post by doctorbighands on 2007-11-08
On a related note: I'm trying to intall the DivX codec to see if that's the issue. Inside the readme file, it gives the following instructions for installation:

"Extract the archive, and run "./install.sh" as root."

So, I navigate to the folder on my desktop, but when I type in...
```

sudo ./install.sh

```

...it shows me the EULA, and nothing installs.

What am I doing wrong?

---

### Post by doctorbighands on 2007-11-08
*bump*

---

### Post by doctorbighands on 2007-11-09
...anyone? Please? C'mon, guys. :)

---

### Post by doctorbighands on 2007-11-09
*bump* once more...

---

### Post by doctorbighands on 2007-11-12
I still need help with this, if anyone can!! Maybe it isn't proper that I keep bumping this thread, but I don't want to start a new one if I can help it.

---

### Post by FuturePilot on 2007-11-12
You might want to look here to make sure you have all of the codecs installed
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by doctorbighands on 2007-11-12
I'm concerned that I may actually have *too many* codecs installed, and some are conflicting with others. Is that possible?

---

### Post by avik on 2007-11-12
I doubt there's a conflict.  The best way to install of course is to get the ubuntu-restricted-extras package, so if you don't have that, get it.  Otherwise, reinstall that package and see what happens.

---

### Post by FuturePilot on 2007-11-12
> **doctorbighands said:**
> I'm concerned that I may actually have *too many* codecs installed, and some are conflicting with others. Is that possible?

I don't think so. The only thing that might be conflicting (although I doubt this is the case) is if you have many video plugins for the browser installed. For example if you have the totem plugin, mplayer plugin and the vlc plugin installed they might conflict with each other

---

### Post by doctorbighands on 2007-11-12
I installed ubuntu-restricted-extras, and that didn't work.

I believe I might have plugins for totem, mplayer, and VLC all installed. How do I check, and how do I narrow it down to just one?

Also, if it helps, it seems to be DivX videos that are causing me the most grief.

EDIT:

I figured out how to find the plugins. I isolated each of them and tried to play a video, but none worked individually any better than all of them installed at once. So, that didn't work. Also, I've tried installing a bunch of DivX codecs using Synaptic, but so far it isn't doing the trick.

---

### Post by doctorbighands on 2007-11-12
Here is a screenshot of what I see when I try to play certain kinds of videos. That blue bar is all I get.

The interesting thing is that the bar only showed up as blue when I took the screenshot. When the video is "playing," I can tell that there's a picture playing inside that vertical area, it's just condensed to that size.

---

### Post by robinl on 2007-11-12
Can you please post the output of ```
about:plugins
``` in Firefox on here?

---

### Post by FuturePilot on 2007-11-12
Just taking a guess here. Try going into synaptic and install totem-xine
Might want to restart Firefox as well afterwards.
Or try the mplayer plugin and remove totem-mozilla

---

### Post by doctorbighands on 2007-11-14
Here are the contents of my "about: plugins" in Firefox:



Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6c Janus, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plugin 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-google-vlc-plugin 	Google VLC plugin 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
Totem Web Browser Plugin 2.20.0

    File name: libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	ogg 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogg 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NSV video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	WMV video 	wms 	Yes
application/asx 	Playlist 	asx 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v


I know this looks a little messy, but I hope it helps you to help me.

---

### Post by skymera on 2007-11-14
try

sudo sh install.sh

---

### Post by doctorbighands on 2007-11-14
When I type that in, I get
```
sh: Can't open install.sh
```

??

---

### Post by shad0w_walker on 2007-11-14
Have you tried disabling compiz? It sometimes causes issues with video playback.

---

### Post by doctorbighands on 2007-11-15
I don't know how to disable compiz. I tried my best, and I ended up losing my title bars. I installed Emerald (does that override compiz?); that gave me back my title bars, and actually ended up making for a significant GUI improvement. Bonus there.

Still can't play DivX videos. I'm not sure, but I think that's the only affected file type. I don't seem to have issues with .wmv, flash, .mov, or .mp4.

---

### Post by shad0w_walker on 2007-11-15
You can turn off compiz from the apperance tool:

System > Preferences > Appearance

It's in the visual effects tab.

---

