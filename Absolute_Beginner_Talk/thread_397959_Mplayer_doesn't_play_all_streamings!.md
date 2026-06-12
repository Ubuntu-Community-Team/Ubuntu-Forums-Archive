---
title: "Mplayer doesn't play all streamings!"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-03-31
Hello,

Could you guide me how I can configure Mplayer to play all video and audio streamings?

Thanks

---

### Post by Maestro23 on 2007-03-31
What formats are you having trouble with?  Have you taken a look at Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by linux-beginner on 2007-03-31
I don't know exactly. I think asf and more.
For example this link:
[http://www.bloomberg.com/tvradio/tv/](http://www.bloomberg.com/tvradio/tv/)
click on Watch now
I see nothing!

---

### Post by Maestro23 on 2007-03-31
> **linux-beginner said:**
> I don't know exactly. I think asf and more.
For example this link:
[http://www.bloomberg.com/tvradio/tv/](http://www.bloomberg.com/tvradio/tv/)
click on Watch now
I see nothing!

Hmm.. Just went there. My mplayer-plugin in FF 2.0.0.3 kicked in after a few seconds and played it fine.

---

### Post by linux-beginner on 2007-03-31
Strange! I've also got mplayer in FF 2.0.0.3!
Any idea?!

---

### Post by Maestro23 on 2007-03-31
Do you have any other browser plugins installed that might be conflicting with the mplayer-plugin?

Does your plugin even attempt to open the stream?

---

### Post by linux-beginner on 2007-03-31
no! mozilla-mplayer is the only installed plugin!
Yes, it attempts to open the stream!

---

### Post by linux-beginner on 2007-03-31
mozilla-mplayer

---

### Post by Campingman on 2007-03-31
I have mplayer plugin on FF 2.0.0.3.  
Will not play this either, 
Reports an error Totem will not play the file type!

---

### Post by Maestro23 on 2007-03-31
> **Campingman said:**
> I have mplayer plugin on FF 2.0.0.3.  
Will not play this either, 
Reports an error Totem will not play the file type!

Ah, Totem is the conflict.  I was having the same problems on some sites.  Uninstalled totem and its plugin(Comes installed w/Feisty) and have had no problems ever since.

Try uninstalling its plugin and see what happens.

---

### Post by Campingman on 2007-03-31
Trouble with that is it tells me I have to uninstall ubuntu desktop to remove Totem or Totem Mozilla.  Now that is just too scary to continue with!

---

### Post by Campingman on 2007-03-31
> **Maestro23 said:**
> Ah, Totem is the conflict.  I was having the same problems on some sites.  Uninstalled totem and its plugin(Comes installed w/Feisty) and have had no problems ever since.

Try uninstalling its plugin and see what happens.

Instead I deleted all Totem plugins from the Mozilla Firefox directory and it still comes up with the Totem error even no plug in is in the file?

---

### Post by Campingman on 2007-03-31
A restart of Firefox did the trick.
Logged in as root, Removed all Totem plugins from the Mozilla Firefox directory (backed up to a separate folder) restarted Firefox and it now plays OK.

---

### Post by Maestro23 on 2007-03-31
> **Campingman said:**
> A restart of Firefox did the trick.
Logged in as root, Removed all Totem plugins from the Mozilla Firefox directory (backed up to a separate folder) restarted Firefox and it now plays OK.

Glad to here :)

---

### Post by linux-beginner on 2007-03-31
I've installed vlc on my ubuntu. Is it possible that vlc causes the problem?!

---

### Post by Maestro23 on 2007-03-31
> **linux-beginner said:**
> I've installed vlc on my ubuntu. Is it possible that vlc causes the problem?!

Did you install the vlc-plugin as well.  I have mplayer w/plugin and vlc (no plugin) on my system.  The mplayer plugin picks up all the embedded video I encounter on the net.

Open up Synaptic and search for "vlc" .  Whatever has a green box beside it is installed.

---

### Post by Campingman on 2007-03-31
I have VLC also and I now play these files OK after removing Totem.  
There is an extension for Firefox called media connectivity that will open a separate media player of your choice to handle files, if you cannot get the plugins to work that may be a solution for you. 
I used to use this and open all files with VLC and it worked just fine.

---

### Post by linux-beginner on 2007-03-31
No. Below, the list of my firefox plugins:
> Windows Media Player Plugin

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
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
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

---

### Post by Campingman on 2007-03-31
Looks pretty similar to mine, I cannot see any obvious differences.  
When you get to the Bloomberg link supplied does it try to do anything?  Does it say Mplayer plug in on the screen when it is loading or is it completely blank?  
It is a pretty slow feed, spends most of the time buffering here
If you go to any other sites, [http://www.apple.com/trailers/](http://www.apple.com/trailers/), does it play any of the trailers here? Does it play with Mplayer plugin?

---

### Post by linux-beginner on 2007-03-31
yes, it tries to play the streaming with mplayer screen of course!
:(

---

### Post by kahrytan on 2007-03-31
I don't know why people keep linking to Restricted Format Wiki.  If you want to play any video file, it's VideoLAN.  It is available in the software repository and will play videos with any codec including WMA.

If you are looking for Flash so you can view YouTube videos, then goto Adobe.com. Adobe Flash is available for Linux. [Easy Ubuntu]("http://easyubuntu.freecontrib.org/") installs it easily too. Easy Ubuntu can also install libdvdcss2 to play dvds but there is legal issues surrounding it. But then again, you do have a right to watch your legally owned dvds on your computer.

---

### Post by Campingman on 2007-03-31
Just trying to determine if you had some sort of conflict or not!

---

### Post by linux-beginner on 2007-03-31
On the site [http://www.apple.com/trailers/](http://www.apple.com/trailers/) I also can't watch films. buffering stops on %99!

---

### Post by Campingman on 2007-03-31
Here is  the link for the media connectivity extension perhaps you will have more success with that
[https://addons.mozilla.org/en-US/firefox/search?q=media+connectivity&status=4](https://addons.mozilla.org/en-US/firefox/search?q=media+connectivity&status=4)

---

### Post by HumbleGod on 2007-04-06
Just wanted to say thanks to all participants in this thread. As a fairly new Ubuntu user, I couldn't figure out why the Mplayer plugin wasn't working in Firefox....turns out it was a conflict with Totem, and following **campingman**'s hints on pg 2 resolved this for me. Thanks again!

---

### Post by rosswmcgee on 2007-04-06
I uninstalled totem and plug ins still can not read Bloomberg.

---

### Post by atze76 on 2007-05-04
If I try to play the bloomberg video, my CPU load goes to 100%... After a few minutes I hear a 1second snipet of the video but then it stops and the CPU load remains at 100% until I close the window. Very weird....

---

