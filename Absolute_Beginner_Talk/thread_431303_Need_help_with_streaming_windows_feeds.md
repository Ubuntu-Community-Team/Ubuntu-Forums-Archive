---
title: "Need help with streaming windows feeds"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by swatF1RESTORM on 2007-05-02
I've just made the full jump to Ubuntu from Windows and I've been having trouble accessing some of the internet streams I could watch using Windows. Mainly NBA.com and XM Radio. I've tryed installing all the plugins that have been recommended in some other posts I've found searching in google but none of them seem to do the trick.

Does anyone know of confirmed settings that work for the site and could lend me a hand? Is there a file I could look up that could confirm my current settings or help diagnose my problem?

swatF1RESTORM

---

### Post by starcraft.man on 2007-05-02
[https://addons.mozilla.org/en-US/firefox/addon/446]("https://addons.mozilla.org/en-US/firefox/addon/446")

That extension is great for configuring totem to stream almost anything, it will find any feeds on a page and list them so you can choose which. 

Should be what your looking for, make sure you have all your codecs installed or are using VLC for streaming.

---

### Post by lbyrd33 on 2007-05-02
I think nba.com is using a mpeg file viewer which in windows would be operated by windows media player. In linux there are a couple of different players that operate mpeg files like totem and mplayer. These also can be made plugins in firefox. You have to install the player, plugin, and the codecs required to view mpeg files.

---

### Post by swatF1RESTORM on 2007-05-03
I have both VLC and Totem installed. I tried using that firefox plugin that starcraft.man recommended. It did succeed in allowing me to choose which (of my 2 players) one I wanted to handle the online media, which was nice. However neither of them worked. VLC would launch and looked like it attempted to load a stream but never displayed any video or audio. Totem launched and then gave me a message about not having permissions to access the stream.

When I go into a type "about : plugins" into the address bar in firefox here is what it lists:

Installed plug-ins

Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.

**Shockwave Flash**

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

**Totem Web Browser Plugin 2.18.1**

    File name: libtotem-basic-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes

**Windows Media Player Plug-in 10 (compatible; Totem)**

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

**DivX® Web Player**

    File name: libtotem-mully-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes

**QuickTime Plug-in 7.1.3**

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes

**VLC Multimedia Plugin**

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

**Java(TM) Plug-in 1.6.0-b105**

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

Does this help anyone identify my problem? I don't really know what I'm looking at but if I had to guess I'd say everything should be working seeing as everything is enabled.

---

### Post by swatF1RESTORM on 2007-05-03
Have I been swept beneath the rug? Or are there just THAT many post?

---

### Post by starcraft.man on 2007-05-03
Sorry, we weren't ignoring you, its just once a thread gets past first page... well, we kinda mostly look at first page :).

Anyway, lets try something different...

Make sure vlc plugin is installed, type this in terminal:
```

sudo aptitude install mozilla-plugin-vlc avahi-daemon avahi-utils
```

Then, run the media player connectivity wizard again... In firefox, Tools > Media Player Connectivity. Select Wizard tab, run it again. Then, let it scan, then change all your formats that appear so that it is VLC playing, VLC should be in the drop down.

Or you can just replace all the location directories so that they read /usr/bin/vlc. VLC should be able to play the silly stream. Hopefully that works.

---

### Post by swatF1RESTORM on 2007-05-03
To: stracraft.man

I hear what you're saying about the first page thingy. Is a bump post considered rude on these forums? I've been to some where people get slightly upset for that and didn't know how it was received on these boards.

I tried what you suggested and it still did not work. I did not fully reboot my system but isn't that supposed to be one of the best things about Ubuntu\Linux? I did restart firefox but was still unable to watch the feed.

[http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/nbatv_top10/top10_070501.asx](http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/nbatv_top10/top10_070501.asx)

Above is the feed I'm trying to get to play. Any other ideas?

---

### Post by starcraft.man on 2007-05-03
> **swatF1RESTORM said:**
> To: stracraft.man

I hear what you're saying about the first page thingy. Is a bump post considered rude on these forums? I've been to some where people get slightly upset for that and didn't know how it was received on these boards.

I tried what you suggested and it still did not work. I did not fully reboot my system but isn't that supposed to be one of the best things about Ubuntu\Linux? I did restart firefox but was still unable to watch the feed.

[http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/nbatv_top10/top10_070501.asx](http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/nbatv_top10/top10_070501.asx)

Above is the feed I'm trying to get to play. Any other ideas?

Nope, not at all rude, how else would we see ones we missed? We can't psychically troll the forums :p (that ability is being worked on in the double super ultra secret Ubuntu labs, but you didn't hear that from me :D)

As for that feed, its a stupid .asx format, from quick glance it looks like another stupid proprietary format, will do a bit of quick research and post back when I find something >.>

EDIT: Gah, I can't seem to find anything for asx, just another silly format that windows pushed out. I don't think the restricted codecs we install contain everything ya need for asx, if I'm wrong can someone correct... I'd like to know a solution to this too.

---

### Post by swatF1RESTORM on 2007-05-03
Anyone else? Ideas? I seemed to be able to get XMradio.com to work for me in Totem although it wasn't as it should be. Once Totem was launched it would say something about not having permission to access the files, however when I would double click on the different items in the sidebar it would come up. XMradoi.com works fine with VLC, but is there a way to not have VLC launch but still have the stream play? NBA.com feeds still aren't working for me still.

---

### Post by sputnick on 2007-05-11
well, i was on break so i went to a site to watch a TV program while i eat, but oh no! it's .asx. next i went to a radio station, it's asx. third try, i went to another radio station, guess what, it's also .asx. 

ok no problem, i can always sing to myself for entertainment, even with my mouth full, anything is better than going back to windows, but just to add my 2 cents to this thread, that someone somewhere somehow might want to hack this proprietary format of microsoft because i'm sure there's a lot of demand for it, i'm sure it's not just the hoops guy and me. 

nick

---

### Post by cntx on 2007-05-16
Hi,

My first forum post here. Fully switched to Ubuntu since the day 7.04 was released.

ASX streaming is the only video format that I have problems with. Everything else plays perfect on Ubuntu.

At present ASX streaming works only as video but NO sound regardless what I do (same problem in Totem and VLC) :( 

Here's an example....Bloomberg TV stream opens, buffers up quickly and plays _**video only**_. Any ideas how to get sound working? Your help would be much appreciated.

[http://www.bloomberg.com/streams/video/LiveBTV200.asx](http://www.bloomberg.com/streams/video/LiveBTV200.asx)

---

### Post by Griffiss on 2007-05-23
Same problem as sputnick. ASX has no audio... 

Is this just something we have to live with (or without) for the time being?

griff

---

### Post by cntx on 2007-05-23
Guys, guys!! I finally FIGURED THIS OUT....woo-hoo :D

OK. Here's what you do. 

Go to HowToForge site, open Ubuntu section, open The Pefect Desktop 7.04 article, go to page 6 and follow instructions on how to install Automatix2.

[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04)

Once Automatix2 has been installed, you open it via** Applications -> System Tools** menu. In Automatix2 you need to load latest codecs from Codecs menu. This installs everything you need to stream Windows media formats. I've tested all the ones posted here (including Bloomberg TV) and all worked perfectly! I'm happy as, especially considering I'm new to Ubuntu (been running it as my primary OS both at home and at work for just over a month).

Enjoy! ;)

---

### Post by Griffiss on 2007-05-23
nice work finding that guide cntx..

but i had a look on ubuntuguide.org, and it discourages the use of automatix:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2)

'Automatix2 is a proprietary script that tries to install some software, and often fails and breaks systems. The Ubuntu community doesn't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu.'

Don't know how seriously to take the warning, but for the time being i don't think i'll try it - any one have info on a safe way of dealing with automatix2?

---

### Post by cntx on 2007-05-24
Griffiss, 

I think you've made a fair point. If Ubuntu is your primary workstation PC and installing any unsupported software on it could result in more headaches than it's worth, then, yes - wouldn't recommend installing Automatix2. Since we are in Beginner's forum, experimenting with various things on Ubuntu may not be such a bad idea. 

From days of Windows I've carried on a habit of taking snapshots of my live system before installing something that could potentially mess things up. Acronis TrueImage does a superb job at snapshotting my current partition at regular intervals (or by manually evoking the backup process). If/when something breaks, I simply go back to the snapshot that I know worked prior to me installing new piece of software that upset my machine. So far I had to restore from Acronis twice in one month. None of those times had anything to do with Automatix2. It was when I edited config files and couldn't back out easily is when I had to rely on Acronis to get me back up and running within 5 minutes. 

So far I've found Automatix2 to be quite good. It installs many programs I didn't know existed under Ubuntu. Once I master how to install all those programs without help of Automatix2 scripts, that's when I can stop using that program. But for now it has resolved many of the issues I had with streaming media codecs and that's what I'm excited about.

---

### Post by Griffiss on 2007-05-29
Yeah fair enough cntx, it's the results that matter and if you have a reliable failsafe like that it should certainly enhance experimentation. i'll give something like that a go.

---

### Post by moore.bryan on 2007-06-18
> **starcraft.man said:**
> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
*this is an AMAZING extension... worked flawlessly on my minimal machine.  tons of thanks starcraft.man.  this extension goes on that list of "cannot do without."*

---

### Post by starcraft.man on 2007-06-18
> **moore.bryan said:**
> *this is an AMAZING extension... worked flawlessly on my minimal machine.  tons of thanks starcraft.man.  this extension goes on that list of "cannot do without."*

LOL, I can't believe this thread came back up its almost 2 months old :p. Your welcome, I never imagined so many people wouldn't know about all the awesome extensions for Firefox. Maybe I should make a list of mine some time... anyway, glad to help :).

---

### Post by moore.bryan on 2007-06-18
[I]i'm pretty selective on installing extensions because my machine is not what one would call stellar, but this one's excellent.

i only have fireftp, mediaplayerconnectivity (now!), menu editor, mouse gestures, secure login, speed dial, and tab mix plus.

[/I]

---

### Post by cntx on 2007-06-18
> **moore.bryan said:**
> *this is an AMAZING extension... worked flawlessly on my minimal machine.  tons of thanks starcraft.man.  this extension goes on that list of "cannot do without."*

This one is definitely the best solution for streaming Windows Media on Ubuntu! Excellent plugin. Works on Swiftfox just as well as Firefox. 

Uber tip, mate! Thanks. ;)

---

### Post by johnraff on 2007-06-18
> **moore.bryan said:**
> *i'm pretty selective on installing extensions because my machine is not what one would call stellar*If you're *that* tight on system resources you might consider using Xubuntu instead of regular Ubuntu. It runs quite nicely for me on only 128MB of Ram. You can just install "Xubuntu desktop" and "Xfce session" appears as an option when you login, so you can compare.

btw I've found installing mplayer plus all the codecs I could get my hands on seems to stream anything I come across OK.

---

### Post by moore.bryan on 2007-06-19
*i've gone way beyond (or would it be below) xubuntu and run a server install with openbox.*

---

### Post by johnraff on 2007-06-21
Ah, cool.
I installed Openbox the other day and when some other things are out of the way plan to give it a try. The *minimal* approach appeals, and maybe a bit more speed...

---

### Post by moore.bryan on 2007-06-21
*i tried all the other light managers (icevm, fluxbox, blackbox, xfce, etc.) and didn't like any of them.  tried openbox and never looked back... good luck.*

---

