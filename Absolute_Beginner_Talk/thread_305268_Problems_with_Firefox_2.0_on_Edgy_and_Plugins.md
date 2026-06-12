---
title: "Problems with Firefox 2.0 on Edgy and Plugins"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by waynepr72 on 2006-11-23
Hi there,

I have read through many peoples helpful notes on this problem but not appear to work, I just can't stream video from the BBC site using wma or Real Audio types. I basically get M-player load and look as it if it is start but then it just stops.  My system set up information is below.  If anyone can see what is wrong here I would appreciate advice.

I have installed all the codecs and Realaudio from Automatixs.

Thanks in advance, Wayne
________________________________________________________________

waynepr72@waynelinux:/usr/lib/mozilla/plugins$ ls -alt
total 8104
drwxr-xr-x 2 root root    4096 2006-11-22 19:25 .
-rwxr-xr-x 1 root root 6904912 2006-11-22 08:38 libflashplayer.so
drwxr-xr-x 3 root root    4096 2006-11-21 22:50 ..
lrwxrwxrwx 1 root root      36 2006-11-21 22:50 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root      37 2006-11-21 22:50 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root      38 2006-11-21 22:50 libtotem-complex-plugin.so -> ../../totem/libtotem-complex-plugin.so
lrwxrwxrwx 1 root root      39 2006-11-21 22:50 libtotem-complex-plugin.xpt -> ../../totem/libtotem-complex-plugin.xpt
lrwxrwxrwx 1 root root      34 2006-11-21 22:50 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root      35 2006-11-21 22:50 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root      36 2006-11-21 22:50 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root      37 2006-11-21 22:50 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root      42 2006-11-21 22:50 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root      43 2006-11-21 22:50 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root  264180 2006-09-13 22:46 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root  264180 2006-09-13 22:46 mplayerplug-in-qt.so
-rw-r--r-- 1 root root  264180 2006-09-13 22:46 mplayerplug-in-rm.so
-rw-r--r-- 1 root root  265008 2006-09-13 22:46 mplayerplug-in.so
-rw-r--r-- 1 root root  264180 2006-09-13 22:46 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root     981 2006-09-13 22:46 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root     981 2006-09-13 22:46 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root     981 2006-09-13 22:46 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root     981 2006-09-13 22:46 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root     981 2006-09-13 22:46 mplayerplug-in.xpt
waynepr72@waynelinux:/usr/lib/mozilla/plugins$ sudo rm libtotem-complex-plugin.xpt
waynepr72@waynelinux:/usr/lib/mozilla/plugins$ sudo rm libtotem-complex-plugin.so 

_____________________________________________________________________


Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 d78

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
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.3.5 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
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

### Post by edmund on 2006-11-23
To get the Realplayer firefox plugin working, install Realplayer - see my comment in:
    [http://ubuntuforums.org/showthread.php?t=300715](http://ubuntuforums.org/showthread.php?t=300715)

Then copy the realplayer files nphelix.so  nphelix.xpt into 
    /usr/lib/firefox/plugins

Then remove the libtotem files from the firefox plugins directory:
    cd /usr/lib/firefox/plugins
    rm libtotem* 
Copy the libtotem* files to a different directory first, just in case.

---

### Post by endre on 2006-11-23
So is Mplayer just unavailable in Firefox 2.0??
All the News sites that base themselves on Windows Media or anything else are simply unavailable!

---

### Post by Circus-Killer on 2006-11-23
i'm not saying this is your problem, but it could be.

basically, some .wmv files will be encoded using DRM (digital rights management). so even if you have support for normal .wmv file and can play them, you still wont be able to play files that makes use of DRM.

this is why we as a community oppose DRM. because in order to view videos protected by DRM we would HAVE to use windows. obviously we heartily disagree with this. companies should find other ways of protecting their video files.

so if you can watch some .wmv files and not others, those others are probably protected by DRM and you might as well give up on those.

---

### Post by tommcd on 2006-11-23
Are you able play videos that you download, but just can't stream them directly in firefox? I had this problem also. Removing the libtotem* plugins worked for some people, but not for me:
[http://ubuntuforums.org/showthread.php?t=289421](http://ubuntuforums.org/showthread.php?t=289421)
I also have 2 mplayer plugin links broken in /usr/lin/firefox/plugins.
[http://ubuntuforums.org/showthread.php?t=289421](http://ubuntuforums.org/showthread.php?t=289421)
[http://ubuntuforums.org/showthread.php?t=283605](http://ubuntuforums.org/showthread.php?t=283605)
Anyway, I finally "fixed" the problem by installing the firefox extension "media player connectivity":
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
This will easily let you choose which video player you want to use to watch video (I use Xine). It then opens the video in a seperate window. Even works on CNN.com.
Hope this helps.

---

### Post by Shane11 on 2006-11-23
Found some interesting stuff on the forum's.
It suggested installing 'Mozilla/Firefox 'media player connectivity' extension.

This I did. Nearly worked first time, had to configure it manually to use Real player10. 
Then it worked ok!

Hope this is of some use to you.:D

---

### Post by Rybo on 2006-11-23
You're initial problem might have been that the plugins didn't have execution permission.

---

### Post by Kubunteando on 2006-11-23
I have found in then mplayer man pages that the -wid option is not valid with the "xv" video driver. This option is used when launching the mplayer from Firefox. So I instead use the "x11" video driver. To change so you can right click the video windows that  opens on the browser, go to configure and set the Video Output to "x11". Or better go to the ".mplayer" folder on you home directory and edit the file "mplayerplug-in.conf" and add a line with "vo=x11".

I can open ASX, and WMV. The BBC works in a weird way: or I hear it or I see it, but not both at the same time. So I copy the link and I paste it in Real Player 10.

I have got quite much help from this forums, so I hope this helps.

---

### Post by Kubunteando on 2006-11-23
I have found in then mplayer man pages that the -wid option is not valid with the "xv" video driver. This option is used when launching the mplayer from Firefox. So I instead use the "x11" video driver. To change so you can right click the video windows that opens on the browser, go to configure and set the Video Output to "x11". Or better go to the ".mplayer" folder on you home directory and edit the file "mplayerplug-in.conf" and add a line with "vo=x11".

I can open ASX, and WMV. The BBC works in a weird way: or I hear it or I see it, but not both at the same time. So I copy the link and I paste it in Real Player 10.

I am using edgy and it works fine. I had multiple problems with mplayer and mplayerplug-in in dapper.
I have got quite much help from this forums, so I hope this helps.

---

### Post by tommcd on 2006-11-24
I had just the opposite. The mplayer plugin worked fine for me in Dapper. No configuring needed. It has never worked for me in Edgy. It must be related to those 2 broken plugin links (mplayerplug-in-gmp.so and mplayerplug-in-gmp.xpt) in /usr/lib/fireox/plugins. I think they are broken because there is no file in /usr/lib/mozilla/plugins for them to link to. Does anyone else have those broken plugin links?
Anyway, media player connectivity gets around the problem just fine. My mplayer works fine, just not the mozilla-mplayer plugin.

---

### Post by waynepr72 on 2006-11-24
Thanks for everyones help on this.  I took the advice to go to the following link and install the MediaPlayerConnectivity from the Mozilla pages below, this lets you configure your players for each file extension, it also has a helpful wizard to check what players you have installed and their paths.  I selected the m-player for ra and wma with the X11 type I think it was and then the video streamed perfectly from the BBC site. All be it in a separate Window but thats not a problem.

[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

Thanks again everyone for your input on this.

Wayne

---

### Post by basslord on 2006-11-29
> Does anyone else have those broken plugin links?
Yes, I 've got those two broken links in Edgy, too. 
But the workaround with the plugin works just fine. Thank you.

rodge

---

