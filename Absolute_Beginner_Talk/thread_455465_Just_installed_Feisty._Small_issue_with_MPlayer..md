---
title: "Just installed Feisty. Small issue with MPlayer."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-26
I used the Feisty Fawn Guide to install everything manually, avoiding to use automatix this time around. Everything works flawlessly for me. However, web sites where I need MPlayer to work are unable to play the video. They're just blank.

When doing a search looking for a solution, I came across this video as an example of a video that doesn't work. However I was unable to find a solution for this issue. I know I'm just missing a small step... but what??

[http://www.hgtv.com/hgtv/pac_ctnt_988/text/0,,HGTV_22056_58466,00.html](http://www.hgtv.com/hgtv/pac_ctnt_988/text/0,,HGTV_22056_58466,00.html)

---

### Post by meng on 2007-05-26
Did you install mplayer plug-in?
Do you still have totem plug-in for Firefox installed (in my experience, this takes precedence over mplayer plug-in)?
Easy way to answer the question is to look at "about:plugins" in Firefox.

---

### Post by Happy_Man on 2007-05-26
Methinks you need flash for that.... not MPlayer.

---

### Post by meng on 2007-05-26
> **Happy_Man said:**
> Methinks you need flash for that.... not MPlayer.
May need both, there's definitely a mplayer-able media file on there though.

---

### Post by Roasted on 2007-05-26
I have flash. Flash is fine.  Youtube works great. Yet... other sites, that don't use flash, don't.

Which plugin might I need?

---

### Post by meng on 2007-05-26
Tell us what you see when you type
about: plugins

into the Firefox address bar
(without the space)

---

### Post by Roasted on 2007-05-26
Long f'n list, but I just copied it all over.





Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.18.1

    File name: libtotem-basic-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.1.3

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6 Janus, copyright 1996-2006 The VideoLAN Team
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
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.31

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

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
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
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
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes
mplayerplug-in 3.31

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

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
application/x-java-applet;jpi-version=1.6 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6 	Java 		Yes

---

### Post by Happy_Man on 2007-05-26
Well, everything seems to be there.....

---

### Post by Roasted on 2007-05-26
Don't know man. It says playing... and on some videos it just says playing forever. Others I get a big red cartoonish looking X over the video. *shrug*

---

### Post by meng on 2007-05-26
I think what may be happening is that the Totem (&/or VLC) plugins are trying to play the file so that the mplayer plugin doesn't get a chance to.
[http://ubuntuforums.org/showthread.php?t=363850](http://ubuntuforums.org/showthread.php?t=363850)

---

### Post by Roasted on 2007-05-26
Okay. I have video now. But my video controls are gone, and I can't right click to "show controls." 

How can I get them back?

---

### Post by p_quarles on 2007-05-26
I've had different problems with MPlayer (when it tries to play DVDs, it shows a frozen opening menu). Not a big enough deal to start a thread, since VLC works fine, but: does anyone think the presence of VLC, Totem and their plugins might have a similar effect on DVDs?

---

### Post by Roasted on 2007-05-26
Not a big enough deal to start a thread? Excuse me? There's an X in the upper right corner. Locate it. Thanks.

On with the topic at hand... 

The reason I want MPlayer to work is for embedded videos on web sites, as already suggested in the very first post of this thread. :) 

VLC? I love VLC. I use it for playing DVDs, music videos, whatever. Can VLC play embedded videos on web sites? If so, I'd like to know how! Besides, right now I'm having an odd issue with VLC. Whenever I play music videos and whatnot on it, it cracks at higher tones. Not sure why. Never did it before...

---

### Post by p_quarles on 2007-05-26
Hi Roasted--I think you took me wrong, and there's really no need for sarcasm. I just thought folks who were following this thread might have some insight into a minor issue I've been experiencing. Sorry if you feel your thread was intruded upon.

---

### Post by Roasted on 2007-05-27
Man. I suck. I thought you were putting down my reasoning to making MY thread saying that I had no reason to make it. My apologies! It's my 21st and I'm... let's just say I'm trying to learn what my limit is! It flew over my head and I took it the wrong way. Sorry bud!

---

### Post by p_quarles on 2007-05-27
No worries, apology accepted, and happy 21st (you're doing WAY better than I was on that day, btw).

---

### Post by gatorchief on 2007-06-03
I just found this thread while looking for the solution to the same issue, and thought I'd pass on how I solved it.  First I tried the installing and un-installing of the mplayer route, but that didn't solve it. Then I installed totem and totem-mozilla, and noticed the embedded video now behaved differently (would reload the buffer, but still no video).  After un-installing the totem-mozilla package, the embedded video started to work correctly. Here is the output from my about:plugins:

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.31

    File name: mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
Shockwave Flash

    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/futuresplash 	Future Splash 	spl 	Yes
Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

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
application/x-java-applet;jpi-version=1.6 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6 	Java 		Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.574 built with gcc 3.4.5 on Nov 30 2005

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes


Hope this helps!

---

### Post by Samjiman on 2007-06-03
> **Roasted said:**
> I used the Feisty Fawn Guide to install everything manually, avoiding to use automatix this time around. Everything works flawlessly for me. However, web sites where I need MPlayer to work are unable to play the video. They're just blank.

When doing a search looking for a solution, I came across this video as an example of a video that doesn't work. However I was unable to find a solution for this issue. I know I'm just missing a small step... but what??

[http://www.hgtv.com/hgtv/pac_ctnt_988/text/0,,HGTV_22056_58466,00.html](http://www.hgtv.com/hgtv/pac_ctnt_988/text/0,,HGTV_22056_58466,00.html)

Hmm...seems like you might have MPlayer, but not the browser plugin.

Try installing through the terminal, like so
```

# sudo apt-get install mplayer-plugin

```

You may have to do an update first though.

---

