---
title: "Instalaction Instruction"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Yuliya on 2007-10-28
I need to install A. Flash Player,and I have the file and the instructions are here:

Installation instructions
.tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.


 but I can't find the option to get to the file. I open the Terminal and then I get stuck... I simply can't find the option that would suit the "navigate to this directory" description. Where exactly do I have to do?

---

### Post by icechen1 on 2007-10-28
You can install flash player by following this: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Browser_Plug-ins)
OFFTOPIC:MY 200TH POST!

---

### Post by Yuliya on 2007-10-28
abosultely marvellous site! Very helpful and with clear instructions. The onyl problem I have now is that even though I installed the flash player, I still can't read the newspaper online. What program do I need exaclty?

---

### Post by icechen1 on 2007-10-28
> **Yuliya said:**
> abosultely marvellous site! Very helpful and with clear instructions. The onyl problem I have now is that even though I installed the flash player, I still can't read the newspaper online. What program do I need exaclty?

What is the site you are trying to get on?

---

### Post by Yuliya on 2007-10-28
[www.latercera.cl](www.latercera.cl) , [www.elmercurio.cl](www.elmercurio.cl) and upload pictures in [www.facebook.com](www.facebook.com)

---

### Post by icechen1 on 2007-10-28
> **Yuliya said:**
> [www.latercera.cl](www.latercera.cl) , [www.elmercurio.cl](www.elmercurio.cl) and upload pictures in [www.facebook.com](www.facebook.com)

did you installed this plugin:
mozilla-plugin-gnash
or this one ? flashplugin-nonfree

---

### Post by Yuliya on 2007-10-28
yes, it says it is installed but still it doesn't work

---

### Post by icechen1 on 2007-10-28
> **Yuliya said:**
> yes, it says it is installed but still it doesn't work

so did you installed the plugin named flashplugin-nonfree or mozilla-plugin-gnash?
you should only install flashplugin-nonfree.

---

### Post by Yuliya on 2007-10-28
both - so should I take the mozilla-thing? (in which case I don't know how to do it)

---

### Post by icechen1 on 2007-10-28
> **Yuliya said:**
> both - so should I take the mozilla-thing? (in which case I don't know how to do it)

in synaptics,uninstall it or do ```
sudo apt-get remove mozilla-plugin-gnash
``` in terminal

---

### Post by Yuliya on 2007-10-28
oh it worked! I can see it now. Thank you sooooooooo much!!!

---

### Post by Yuliya on 2008-01-17
I have a new computer now and I have the same problem - but I've done everything it says here and still, I can't watch the newspaper. What can it be? I have installed both thing and check that the other one is not installed - but as I said, the newspaper still can't be seen.

---

### Post by Yuliya on 2008-01-20
Please, could somebody help me!?

I want to watch some files, not just the Newspaper now and I just can't see it. It's like "downloading" but it never goes out of that states and I've installed everything that was on this thread. This is what I have:

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.1, the GNU Flash Player. Copyright © 2006 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
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
GCJ Web Browser Plugin 0.92

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	GCJ 	class,jar 	Yes
application/x-java-applet 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-applet;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
application/x-java-bean 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-bean;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
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

---

