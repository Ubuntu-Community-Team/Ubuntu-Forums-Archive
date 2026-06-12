---
title: "New install, flash player broken"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by i3ear on 2008-01-16
First things first, this used to be another thread so forgive all the other posts, I just personally hate spam

Now, there are two computers in my household, my moms computer (Win XP SP2) And this computer (Ubuntu 7.10 or whatever)

Now the trick is how do I get all my old stuff (that I transferred to my moms computer before I reformatted) into this computer?


Personally I was thinking windows shared folder, but blah. Whatever works the quickest.

---

### Post by nikoPSK on 2008-01-16
The Flash plugin installation is currently broken. This is due to Adobe changing the tar file that the package downloads. See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) if you need to fix this immediately, but it's recommended to wait for an official fix.

---

### Post by i3ear on 2008-01-16
Alright, how do I remove Gnash?

Edit: AKJSHDFKLASHFnevermind

---

### Post by SunnyRabbiera on 2008-01-16
you might have to stick to the flash player in the repositories.
also if you need mp3 playback we can help you out there too.

---

### Post by wolfen69 on 2008-01-16
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by i3ear on 2008-01-16
404
and I have no idea how to install files in general

Edit: Nevermind got it fixed, thanks alot
This **** is damn confusing though.

Now, so I do not spam, I am gonna edit this topic some more for my second quesion

---

### Post by nikoPSK on 2008-01-16
> **i3ear said:**
> 404
and I have no idea how to install files in general

Edit: Nevermind got it fixed, thanks alot
This **** is damn confusing though.

Now, so I do not spam, I am gonna edit this topic some more for my second quesion

sorry what? :confused:

---

### Post by NTesla on 2008-01-16
[http://mirror.ne.gov/ubuntu/pool/mul....7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/mul....7.10_i386.deb)

the flash installation file in this link gives error for amd64 architecture since it is for x86. Is there a flash plugin for AMD64? 

My problem is not to be able to run videos on google video. I installed mplayer plugin and youtube works fine, but I cannot get google video work. 

Any help will be appreciated.

---

### Post by nikoPSK on 2008-01-16
> **NTesla said:**
> [http://mirror.ne.gov/ubuntu/pool/mul....7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/mul....7.10_i386.deb)

the flash installation file in this link gives error for amd64 architecture since it is for x86. Is there a flash plugin for AMD64? 

My problem is not to be able to run videos on google video. I installed mplayer plugin and youtube works fine, but I cannot get google video work. 

Any help will be appreciated.

google video should play if youtube is working...?

---

### Post by CCNA_student on 2008-01-16
NTesla, if you want the 64-bit version of Adobe Flash Player look here for instructions at [http://ubuntuforums.org/showthread.php?t=368607]("http://ubuntuforums.org/showthread.php?t=368607")
And if the person unable to install Adobe Flash Player x86 wants it just go to adobe.com and click on the little get Flash Player icon. All you have to do is download the tar.bz file, unzip it, double click on the file called flashplayer-installer and run it in the terminal when Ubuntu asks what to do. This worked for me.

---

### Post by NTesla on 2008-01-17
Thanks for the advice, I'll try it, but do you think that's the reason why I cannot play google video although I can play youtube. And below is my about:plugins for the record:

Shockwave Flash
MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

DivX Browser Plug-In
MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes

QuickTime Plug-in 6.0 / 7
MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes

RealPlayer 9
MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes

Windows Media Player Plugin
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

mplayerplug-in 3.40
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
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes

---

