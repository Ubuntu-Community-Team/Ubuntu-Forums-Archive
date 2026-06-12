---
title: "Video players being wierd!"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Alistair1234 on 2007-11-19
When opening a video in any player (vlc, mplayer, totem) it starts to play, then after about 10 secs the player window fades and goes black and white and the video stops. Attempting to close produces the force quit option which works. Also, firefox crashes when watching youtube / flash videos but then restoring the firefox session causes the video to play (the next video does the same thing though)?!

The strange thing is that all the videos were working fine earlier but now they dont - no restart or anything.

What is going on?!

Any help would be greatly appreciated.

(I'm running ubuntu 7.10 and have nvidia 8600gt which seems to work ok)

---

### Post by philinux on 2007-11-19
In the address bar of firefox type about:config and post the results.

edit - ```
about:plugins
```

---

### Post by Alistair1234 on 2007-11-19
that produces a massive list of stuff and i cant select any of it to copy etc. sorry if im being thick!

---

### Post by zabien1970 on 2007-11-19
Can you right click on the page > left click select all then right click again > copy
then when you go to post a reply left click > paste
Make sure you click the # icon on the reply page to wrap the text

---

### Post by Alistair1234 on 2007-11-19
i can only select one line at a time

---

### Post by philinux on 2007-11-19
just hold your mouse left key down and run it down the page.

---

### Post by zabien1970 on 2007-11-19
He's right, I tried to copy mine, wouldn't work? Hmmm

---

### Post by Alistair1234 on 2007-11-19
It won't let me. it just selects one line at a time. Nothing works to get hold of more than one line (ctrl-click, shift dn arrow, mouse select)

---

### Post by philinux on 2007-11-19
This has always bugged me, haha,,

Once you got the plugins displayed select File -  Save page as

Then you can upload it in a reply.

---

### Post by Alistair1234 on 2007-11-19
edit => select all does nothing too

---

### Post by Alistair1234 on 2007-11-19
It saved as a .xul file and the forum says it is an invalid file?!

---

### Post by philinux on 2007-11-19
I save mine as html but then had to right click create archive then upload the archive.

The reason this is better is that some formating is retained making it easier to read.

I have no problem selecting Edit Select all - it just selects all the text as normal.

The other way I've seen is pressing shift print screen to take screen shot several time to get it all.

---

### Post by Alistair1234 on 2007-11-19
Right. tried that for both. hope they are ok.

---

### Post by philinux on 2007-11-19
Doh and double doh,

Meant ```
about:plugins
```.

Must be having a bad day soz.

---

### Post by Alistair1234 on 2007-11-19
No probs. this is what i got:

```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
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
video/x-m4v 	MPEG-4 video 	m4v 	Yes
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

```

---

### Post by philinux on 2007-11-19
Well that looks identical to mine so why firefox is behaving badly is odd.

Have you any addon installed for firefox.

---

### Post by Alistair1234 on 2007-11-19
I have installed the download helper 2.5  add on and firefox doesnt seem to crash as easily. Its when the videos are player outside the browser that things go wierd!

The video keeps playing for a few seconds in grayscale (like the window goes) and then freezes.

---

### Post by philinux on 2007-11-19
That sounds like a graphics card problem then.

Are these videos you've downloaded and are on your desktop?

---

### Post by zabien1970 on 2007-11-19
Don't know if this will help but my system won't play certain media like dvd's with compiz running
alt f2 then  metacity -- replace allows me to run them, I know its not a fix just a workaround but it works

---

### Post by Alistair1234 on 2007-11-19
I have heard stuff about the 8600gt being a bit of a pain but compiz and everything else is running fine. The rest of the system is completely unaffected - its just the video window which fades - and it was doing it before I installed the graphics card (ATI onboard graphics)!

---

### Post by MegaJim on 2007-11-19
There seems to be a problem with the 2d acceleration on some restricted drivers with compiz, I think having the proper xgl libraries may help with this but I can't test it as my laptop doesn't have the capability to run compiz - as another poster suggests switching to metacity temporarliy to watch videos will work.

---

### Post by Alistair1234 on 2007-11-19
the videos are downloaded ones and ones I had on file already (various formats). I cant get ubuntu to see my cd/dvd drive so not sure if it affect that as well (but thats a whole other can of worms!)

---

### Post by philinux on 2007-11-19
As a start turn compiz off and see if videos play ok.

---

### Post by Alistair1234 on 2007-11-19
Without compiz the videos play ok with no greying of the window/screen etc but I am unable to use any of the menus and buttons in the player and the only way to exit is to "force quit"

---

