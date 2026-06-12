---
title: "Listen to radio from Gutsy"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by mmasroorali on 2008-01-12
I have been using Ubuntu for my office computer (I use Fedora at home) for the last three months. Somehow, I fail to listen to radio from Ubuntu.

I have realplayer installed. Inside Mozilla, I get a popup window which says that it is connecting, and then its stops. 

I also tried banshee, that also did not succeed. 

What is it I am missing here?

Can I get a step by step instruction on how to listen to radio from Ubuntu? I am behind a proxy which only listens to 3128 port. Other people are listening the radio from the same network using Windows XP and having a field day teasing me (me being the local Linux advocate here). 

If I can listen to [http://www.bbc.co.uk/worldservice/](http://www.bbc.co.uk/worldservice/) that will be sufficient. 

Thanks in advance.

---

### Post by philinux on 2008-01-12
[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

The bottom link on this page is the feisty deb package. Use this as the gutsy one has a slight bug whereby the helix dna plugin which does the rm audio streaming fails to get installed properly. It's a bug at launchpad.

Uninstall the version of realplayer you got now.

---

### Post by dburnett77 on 2008-01-12
Try XMMS which you can install via Synaptic:
Website is:

[http://www.xmms.org/](http://www.xmms.org/)

and, look at:

[http://support.bbc.co.uk/ogg/ogg-xmms.shtml](http://support.bbc.co.uk/ogg/ogg-xmms.shtml)

for help listening behind a proxy.  There's also a configure option for MP3 selection.

---

### Post by laidback on 2008-01-12
Yesterday I installed (on 7.10) realplayer plugins via the BBC iplayer web site. This worked, my trials via Helix didn't. Radio and TV are both working. Needed to reopen Firefox a couple of times to get rid of the message that I needed additional plugins even though it was working by this time.

---

### Post by ubuntu-freak on 2008-01-12
I can do all my streaming with just mplayer and helix, including the BBC.
 
Check out my how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
It WILL work. Give BBC radio time to load though.
 
Nathan

---

### Post by mmasroorali on 2008-01-13
I have followed the instructions in [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) to the letter.

Unfortunately, the results are the same as before. In Mozilla, I get a window which says Getting playlist, then its says Stopped. This happens every time I click on the play button. 

What is it I am missing here?

How to debug the problem? A dedicated user of Unix/Linux for 17 years, this is very frustrating for me.

On a similar issuer, did anybody have any luck downloading the player at [www.real.com/linux](www.real.com/linux), for my case, I simply get an empty page.

---

### Post by philinux on 2008-01-13
See post #2 this works for me.

And check 

```
about:plugins
```

In firefox.

---

### Post by ubuntu-freak on 2008-01-13
> **mmasroorali said:**
> I have followed the instructions in [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) to the letter.

Unfortunately, the results are the same as before. In Mozilla, I get a window which says Getting playlist, then its says Stopped. This happens every time I click on the play button. 

What is it I am missing here?

How to debug the problem? A dedicated user of Unix/Linux for 17 years, this is very frustrating for me.

On a similar issuer, did anybody have any luck downloading the player at [www.real.com/linux](www.real.com/linux), for my case, I simply get an empty page.

 
Some people have to remove a certain file from the /home/.firefox folder. I don't remember what though. Save your bookmarks and delete the folder, then reinstall FF and mozilla mplayer, helix plugins. Then check your config is the same (should be). Did you remove Realplayer? Should've been removed automatically when Helix was installed though.
 
Nathan

---

### Post by kelvin spratt on 2008-01-13
I personally use streamtuner and Xmms always works for me.

---

### Post by ubuntu-freak on 2008-01-13
> **kelvin spratt said:**
> I personally use streamtuner and Xmms always works for me.

 
I guess having a back up for radio is good. Just surprises me that people don't know all they need for video streams is mplayer, and helix (through mplayer) for ram radio. 
 
Nathan

---

### Post by mmasroorali on 2008-01-14
This is what I have done after your very last post.
     1. Removed the /home/.mozilla folder (did not bother backing up the bookmarks).
     2. Installed libdvdcss2, libdvdcss2-dev. 
     	Reinstalled w32codecs. 
     3. Uninstalled totem-mozilla (in fact it was already uninstalled)
     	Uninstalled mozilla-plugin-vlc (again already uninstalled)
     4. Updated my system. It was already updated.
     5. Removed realplayer (and realplay).
     6. Removed firefox (a few other dependents were removed).
     7. (Re)Installed firefox.
     8. Installed 
          mplayer mozilla-mplayer helix-player mozilla-helix-player
	Some of these were already installed.
     9. Edited the /etc/mplayerplug-in.conf. Replaced all the contents with those suggested in [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833).
     10. Opened [http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/). And the clicked on Listen to World News Bulletin. 
     11. I get a new window with title [http://www.bbc.co.uk/-](http://www.bbc.co.uk/-) BBC Media Player - Mozilla Firefox. This window says, 
     	 Getting Playlist, 
	 Playing rtsp://rm.bbc.c ..  (quickly goes away), then 
	 Stopped. 
	 
	 Pressing the play button gives me the same result.
     12. I even rebooted the machine (may be a superstition)
     13. I tried 
     	 i) Standard quality (my Internet connection speed is moderate), Windows media player and 
	 ii)Standard quality, Real player
	 Both gave the same result. 

	 Waiting for a long period with this window open did not improve anything (loading time? but nothing was happening there).

My proxy settings are 172.20.0.1:3128. Other people are using the same proxy to listen to BBC using Windows XP.

I do not know what to do.

Output from about:plugins

STARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTARTSTART

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.40

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
    mplayerplug-in 3.40

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
    mplayerplug-in 3.40

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
mplayerplug-in 3.40

    File name: mplayerplug-in.so
    mplayerplug-in 3.40

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
audio/x-scpls 	Shoutcast Playlist 	pls 	Yes

ENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDENDEND

---

### Post by ubuntu-freak on 2008-01-14
Was it the ram stream you tried to play? It should work. Keep tinkering with it. Me and others can listen to radio with my how-to so don't give up. 
  
Do apple.com streams work?


Nathan

---

### Post by mmasroorali on 2008-01-14
Yes, on both counts.

The streams from BBC has the extension ram.

Videos at apple.com work (extension 3gp), without the slightest problem. Single click resulted in playing them.

I do not know how to tinker my system to make it work with BBC. What else can I tinker?

---

### Post by philinux on 2008-01-14
Looked at your about plugins. The one thing your missing is the helix dna plugin that is needed to play the rm streams that the bbc uses.

[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

The bottom link is the feisty deb for realplayer which correctly installs the helix dna plugin.

---

### Post by mmasroorali on 2008-01-14
Finally it works!!!

I installed [http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/). Had to uninstall helix-player and mozilla-helix-player  for conflict in a library.

Then lo and behold, it works. 

Now, if I want to do it for another person (in another computer), what would the precise things to do? I did and undid so many things.

May be the simple things in the first part of this post?

---

### Post by ubuntu-freak on 2008-01-14
> **mmasroorali said:**
> Finally it works!!!

I installed [http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/). Had to uninstall helix-player and mozilla-helix-player  for conflict in a library.

Then lo and behold, it works. 

Now, if I want to do it for another person (in another computer), what would the precise things to do? I did and undid so many things.

May be the simple things in the first part of this post?

 
You don't need realplayer. Helix is realplayer and the win32codecs give it support for rm and ram. I listen to BBC radio all the time and I've never installed realplayer.
 
I updated my how-to today. You might have had a plugin installed that needed removing or firefox's plugin dat file needed deleting.
 
[http://www.gnome-look.org/content/show.php/GNUtoon?content=70206](http://www.gnome-look.org/content/show.php/GNUtoon?content=70206)
 
Nathan

---

### Post by ubuntu-freak on 2008-01-14
> **philinux said:**
> Looked at your about plugins. The one thing your missing is the helix dna plugin that is needed to play the rm streams that the bbc uses.

[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

The bottom link is the feisty deb for realplayer which correctly installs the helix dna plugin.

 
Just to correct a common misconception, you do not need 'Reals' RealPlayer to play rm video and ram radio  streams. Helix plugin + mplayer plugin + win32codecs is all you need, and the correct 'enable' settings in mplayer's plugin config.
 
I've never had Realplayer installed in Gutsy and passed all the online tests and I listen to BBC ram radio.
 
Nathan

---

### Post by mmasroorali on 2008-01-15
> **reassuringlyoffensive said:**
> You don't need realplayer. Helix is realplayer and the win32codecs give it support for rm and ram. I listen to BBC radio all the time and I've never installed realplayer.
 
I updated my how-to today. You might have had a plugin installed that needed removing or firefox's plugin dat file needed deleting.
 
[http://www.gnome-look.org/content/show.php/GNUtoon?content=70206](http://www.gnome-look.org/content/show.php/GNUtoon?content=70206)
 
Nathan

I do not know what is going wrong, but after following [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) to the letter (UPDATED), BBC does not work anymore. I even tried with a fresh machine with gutsy freshly installed. That even did not help.


This problem would have been over long time back. With my fairly long experience this situation is utterly ridiculous.

Can not ask for help since I do not know what to ask for. This is affecting my regular work, but can not give up this prestige issue (prove that Linux is usable for everything).

Frustration, frustration.

---

### Post by ubuntu-freak on 2008-01-15
> **mmasroorali said:**
> I do not know what is going wrong, but after following [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) to the letter (UPDATED), BBC does not work anymore. I even tried with a fresh machine with gutsy freshly installed. That even did not help.


This problem would have been over long time back. With my fairly long experience this situation is utterly ridiculous.

Can not ask for help since I do not know what to ask for. This is affecting my regular work, but can not give up this prestige issue (prove that Linux is usable for everything).

Frustration, frustration.

 
What plugins are listed when you type about : plugins (no spaces) in the firefox address bar?

---

### Post by philinux on 2008-01-15
It seems for some people the helix dna plugins dont get picked up by firefox correctly.

[https://bugs.launchpad.net/ubuntu/+source/helix-player/+bug/147505](https://bugs.launchpad.net/ubuntu/+source/helix-player/+bug/147505)

However I tried the helix route. Failed would not play rm from bbc. Installing the feisty deb of realplayer ( I dont use realplayer itself by the way) correctly installs the helix plugin. Why how what who knows but it just does.

---

### Post by ubuntu-freak on 2008-01-15
> **philinux said:**
> It seems for some people the helix dna plugins dont get picked up by firefox correctly.

[https://bugs.launchpad.net/ubuntu/+source/helix-player/+bug/147505](https://bugs.launchpad.net/ubuntu/+source/helix-player/+bug/147505)

However I tried the helix route. Failed would not play rm from bbc. Installing the feisty deb of realplayer ( I dont use realplayer itself by the way) correctly installs the helix plugin. Why how what who knows but it just does.

 
Once you delete the firefox plugin dat file, reinstall firefox, mplayer and helix plugins the ram radio should work. I even tested some french station.
 
So odd. I used these settings and setup in Debian and they worked instantly in Ubuntu too. I haven't had reals realplayer or anything of theirs for almost a year. 
 
Nathan
 
Edit: MPlayer doesn't need realplayer or helix for rm video by the way, just for audio streams. It just needs w32codecs and the 'enable rm' option.

---

### Post by philinux on 2008-01-15
Odd indeed. In fact doing it with the gutsy version of realplay didn't work either. I jut tried the feisty deb cos I knew it worked previously. 
I could see the nphelix.so files were in the correct place but firefox refused to report them in about: plugins.

I would have gone with your method had it been shown to me last November. But as they say if it aint broke dont fix it, I think I'll leave my setup alone. :)

---

### Post by ubuntu-freak on 2008-01-15
> **philinux said:**
> Odd indeed. In fact doing it with the gutsy version of realplay didn't work either. I jut tried the feisty deb cos I knew it worked previously. 
I could see the nphelix.so files were in the correct place but firefox refused to report them in about: plugins.

I would have gone with your method had it been shown to me last November. But as they say if it aint broke dont fix it, I think I'll leave my setup alone. :)

 
It wont hurt to add my settings to your mplayerplug-in.conf.
 
You wont regret it. 
 
Nathan

---

### Post by philinux on 2008-01-15
> **reassuringlyoffensive said:**
> It wont hurt to add my settings to your mplayerplug-in.conf.
 
You wont regret it. 
 
Nathan

You dont think I'm that slow, did that days ago. :lolflag:

---

### Post by ubuntu-freak on 2008-01-15
> **philinux said:**
> You dont think I'm that slow, did that days ago. :lolflag:

 
Oh did you? Haha great. Someone told me they had to delete the Firefox plugin dat file about a dozen times and then it worked!
 
It's a Firefox bug. It should refresh and isn't until you keep kickin its ****.
 
Nathan

---

### Post by philinux on 2008-01-15
> **reassuringlyoffensive said:**
> It wont hurt to add my settings to your mplayerplug-in.conf
Nathan

Tell you what that did it enabled full screen for whats it's worth. Before the video would get slowmo then when switching back to normal size the vid would go fast forward and catch up. Meanwhile the audio would run spot on. Mind you i was told, early days, to set vo=x11. If I set it to anything else I get no play. Maybe old machine?

---

### Post by ubuntu-freak on 2008-01-15
> **philinux said:**
> Tell you what that did it enabled full screen for whats it's worth. Before the video would get slowmo then when switching back to normal size the vid would go fast forward and catch up. Meanwhile the audio would run spot on. Mind you i was told, early days, to set vo=x11. If I set it to anything else I get no play. Maybe old machine?

 
I had to use x11 (with compiz running) before I did
 
**sudo dpkg-reconfigure xserver-xorg**
 
X11 is poop. Xv is great. 
 
Also, you don't need vo= in the conf, you can set it in the main player.
 
Nathan

---

### Post by Drakkor on 2008-01-15
I just got it to work in streamtuner,a great program,by the way, just did a search for bbc ,in  shoutcast,and it came up !   :)

---

### Post by ubuntu-freak on 2008-01-15
> **Drakkor said:**
> I just got it to work in streamtuner,a great program,by the way, just did a search for bbc ,in  shoutcast,and it came up !   :)

 
It's satisfying to get it all working in Firefox though:)

---

### Post by mmasroorali on 2008-01-15
> **reassuringlyoffensive said:**
> What plugins are listed when you type about : plugins (no spaces) in the firefox address bar?

This the output (deleted my mozilla directory and rebooted my machine before doing this)

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
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
Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.40

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
    mplayerplug-in 3.40

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
    mplayerplug-in 3.40

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
mplayerplug-in 3.40

    File name: mplayerplug-in.so
    mplayerplug-in 3.40

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
audio/x-scpls 	Shoutcast Playlist 	pls 	Yes

---

### Post by ubuntu-freak on 2008-01-15
I see a lot of yes's so that's good. Didn't look like 'about : plugins' in FF though. Did it another way?
 
Why have Gnash? The adobe one works better.
 
I added xine-plugin to the remove part. Could be installed on your system so try removing that.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Do a google search for 'realplayer test' and see how they work. Try and play an ram radio stream from your country too.
 
Nathan 
 
BTW: It's the plugin dat file you delete if FF doesn't pick up your plugins, one guy told me he had to delete it about a dozen times. It's a Firefox bug. It's delailed at the 'IMPORTANT' section of my how-to

---

### Post by mmasroorali on 2008-01-16
> **reassuringlyoffensive said:**
> I see a lot of yes's so that's good. Didn't look like 'about : plugins' in FF though. Did it another way?
 
Why have Gnash? The adobe one works better.
 
I added xine-plugin to the remove part. Could be installed on your system so try removing that.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Do a google search for 'realplayer test' and see how they work. Try and play an ram radio stream from your country too.
 
Nathan 
 
BTW: It's the plugin dat file you delete if FF doesn't pick up your plugins, one guy told me he had to delete it about a dozen times. It's a Firefox bug. It's delailed at the 'IMPORTANT' section of my how-to

This is not related to the issue (hopefully), but as was suggested by you I removed gnash.

xine-plugin was not installed. I had followed your latest howto.

Now about the tests,

Realplayer test failed 
    [http://service.real.com/test/](http://service.real.com/test/) (behaves the same as BBC)
    [http://www.udel.edu/UMS/itv/realplayer/test.html](http://www.udel.edu/UMS/itv/realplayer/test.html) (behaves the same as BBC)
    

Passed the test at
    [http://www.digital-one.fi/realplayer.html](http://www.digital-one.fi/realplayer.html)
   

Then I tried pasting the link [http://www.bbc.co.uk/bengali/meta/tx/nb/beng_provati_au_nb.ram](http://www.bbc.co.uk/bengali/meta/tx/nb/beng_provati_au_nb.ram) directly to helix (open URL)

This gave a message in the line that, the player does not have the capabilities to ..., This component is supported by RealPlayer. It clearly mentioned that the following components are required, 
           protocol_rtsp_rdt

This also had the option to get RealPlayer. Which when clicked a Browser page
was launched (konquerer).

This eventually lead the downloading
     realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin 

I installed this and had to set the proxy. I had even to coax RealPlayer to use HTTP for all content (RTSP and PNA).

And now Directly pasting the link worked.

To make the online tests work, I had to uninstall helix-player (and plugin), mozilla-mplayer plugin. Then everything worked, including BBC.

All the online tests mentioned before were then successful.

In my experience if both mplayer-mozilla (plugin) and RealPlayer are installed, BBC will not work. And I was not successful in making mplayer work for BBC.

Well, there may be other opinions but this was what happened in my case. I could even repeat the procedure successfully in another computer run by a Linux enthusiast.

Short summary description in making my system successful, 

      1. Install RealPlayer from
      [https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/). You may
      require to install libstdc++5, use synaptic.  

      2. Set proxy (if necessary) and transports (HTTP) in RealPlayer.
      
      3. Set proxy in mozilla (if necessary).

Then try the online tests using RealPlayer test in Google.

My sincerest thanks to all those who helped my in the last couple
days. They were real supports in my frustrations.

---

