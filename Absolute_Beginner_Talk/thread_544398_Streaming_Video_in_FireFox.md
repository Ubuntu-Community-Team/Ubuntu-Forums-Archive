---
title: "Streaming Video in FireFox"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-09-06
Hello,

I used to be able to stream movie trailers from Apples web site and also play all other streaming video. Now all that I can watch is flash. The following plugins are in: /usr/lib/mozilla-firefox/plugins

flashplayer.xpt            libtotem-mully-plugin.xpt
libflashplayer.so          libtotem-narrowspace-plugin.so
libjavaplugin.so           libtotem-narrowspace-plugin.xpt
libtotem-basic-plugin.so   libunixprintplugin.so
libtotem-basic-plugin.xpt  nphelix.so
libtotem-gmp-plugin.so     nphelix.xpt
libtotem-gmp-plugin.xpt    nppdf.so
libtotem-mully-plugin.so

Like I said just yesterday I was able to watch all of this and today it all stopped working. And the wife claims she did nothing to it when I was at work but a beg to differ :)

---

### Post by FuturePilot on 2007-09-06
```
ls /usr/lib/firefox/plugins/
```
Make sure all of those are present there too.

---

### Post by Malice007 on 2007-09-06
Yes they are:

ls /usr/lib/firefox/plugins/
flashplayer.xpt            libtotem-mully-plugin.xpt
libflashplayer.so          libtotem-narrowspace-plugin.so
libjavaplugin.so           libtotem-narrowspace-plugin.xpt
libtotem-basic-plugin.so   libunixprintplugin.so
libtotem-basic-plugin.xpt  nphelix.so
libtotem-gmp-plugin.so     nphelix.xpt
libtotem-gmp-plugin.xpt    nppdf.so
libtotem-mully-plugin.so

---

### Post by philinux on 2007-09-06
In the firefox address bar type

  about:plugins 

Just to check what firefox thinks it has installed.

---

### Post by LowSky on 2007-09-06
> **philinux said:**
> In the firefox address bar type

  about:plugins  [edit] for some reason the colon and p is appearing as a smiley ? its supposed to be about colon plugins 

Just to check what firefox thinks it has installed.


```
 about:plugins 
```


:p  ....i love the forums

---

### Post by Malice007 on 2007-09-06
ok here is that info:

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.630 built with gcc 3.3.5 on Aug 6 2007

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

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
Adobe Reader 7.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
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

### Post by Malice007 on 2007-09-06
Any help on what happend?

---

### Post by philinux on 2007-09-06
Ok your using totem plug in I use mplayer but you've got mov enabled.

What happens when you try to play a movie trailer? Any errors or messages?

---

### Post by Malice007 on 2007-09-06
No Errors I just get the player but when I hit play nothing, here is a image of what I see:

---

### Post by philinux on 2007-09-06
[http://movies.apple.com/movies/independent/hatchet/hatchet_h480.mov](http://movies.apple.com/movies/independent/hatchet/hatchet_h480.mov)

Ok this is the link to the trailer I just right clicked and copied url.

Open totem movie player and select Movie open location and see if stand alone totem can actually play this.

---

### Post by Malice007 on 2007-09-06
Yes it works

---

### Post by Malice007 on 2007-09-06
Here is a pic of what edit/pref/content/filetypes/manage in firefox also:

---

### Post by philinux on 2007-09-06
The problem with the default firefox settings is that you cant see how it manages file type unless there's an association. do this.

1) Type about:config in the address bar
2) look for the option browser.download.hide_plugins_without_extensions
3) Change its value from true (default) to false by double clicking on it
4) Then go into pref manage and see whats it doing with quicktime files.

Other than that unless someone with more experience can help cant think what to do.

By the way I had so much bother with the totem firefox plugin I got rid of it and installed mplayer plugin. Had no bother at all.

---

### Post by dwhitney67 on 2007-09-06
I want to add that I am having the same problem.  The video clip provided plays fine in the standalone Totem Movie Player, but within Firefox I never receive any data to be displayed... the pop-up window just sits there "waiting" for data to be received.

---

### Post by philinux on 2007-09-06
There is a work around until someone else chimes in with a solution. Other than dumping totem for mplayer and thats this addon. Mediaplayerconnectivity.

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

I have it installed but disabled. Just in case I get any weird behaviour. :lolflag:

---

### Post by dwhitney67 on 2007-09-06
> **philinux said:**
> There is a work around until someone else chimes in with a solution. Other than dumping totem for mplayer and thats this addon. Mediaplayerconnectivity.

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

I have it installed but disabled. Just in case I get any weird behaviour. :lolflag:

Per your suggestion, I installed the firefox addon.  It doesn't work.  I get this error when attempting to view the video clip:

*Error opening/initializing the selected video_out (-vo) device.*

Any ideas?

---

### Post by philinux on 2007-09-06
You did close and restart Firefox?

---

### Post by dwhitney67 on 2007-09-06
yes, I restarted per the instructions presented to me after installing the add-on.

---

