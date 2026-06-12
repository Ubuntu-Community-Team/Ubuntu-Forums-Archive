---
title: "Flash Player won't install on Ubuntu 7.10"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by rachel10123@msn.com on 2008-02-08
Flash Player won't install on Ubuntu 7.10,I have searched the web and Ubuntu to help me with this but everything I have tried has failed me.:confused:

---

### Post by philinux on 2008-02-08
[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

The first link is the easiest. Just make sure gnash is uninstalled.

---

### Post by rachel10123@msn.com on 2008-02-08
Thanks for your help,but this doesn't work.

Anymore ideas?

---

### Post by jan quark on 2008-02-08
run this in terminal

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by gandaran on 2008-02-08
> **rachel10123@msn.com said:**
> Flash Player won't install on Ubuntu 7.10,I have searched the web and Ubuntu to help me with this but everything I have tried has failed me.:confused:

try this one at a time (assuming you have the repos enabled)
       
     sudo apt-get remove flashplugin-nonfree
      
     sudo apt-get update   

     sudo apt-get install flashplugin-nonfree

also this just to make sure you didn't play around with gnash

     sudo apt-get remove gnash

---

### Post by rachel10123@msn.com on 2008-02-08
I know I am appearing really ignorant.

But it says it has installed, but when I restart my browser. I cannot play games on candystand.com 

But sites like youtube work.

---

### Post by philinux on 2008-02-08
Ok, in the firefox address bar type

```
about:plugins
```
Then press enter.
Post the results back here using cut and paste.

---

### Post by rachel10123@msn.com on 2008-02-08
Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r115

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.626 built with gcc 3.2.0 on Jul 26 2007

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
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

---

### Post by philinux on 2008-02-08
Well that looks ok from here. 

I'd reboot the pc.

---

### Post by gandaran on 2008-02-08
> **rachel10123@msn.com said:**
> I know I am appearing really ignorant.

But it says it has installed, but when I restart my browser. I cannot play games on candystand.com 

But sites like youtube work.

I looked up candystand.com, I also cannot play those games.I think it's flash embedded in java, it's something linux cannot play yet, maybe I'm wrong.

---

### Post by philinux on 2008-02-08
> **gandaran said:**
> I looked up candystand.com, I also cannot play those games.I think it's flash embedded in java, it's something linux cannot play yet, maybe I'm wrong.

I tried it and it works fine. The OP also has java installed and its the same as mine, so to is the flash plugin. Lets hope a reboot sorts it. :)

---

### Post by rachel10123@msn.com on 2008-02-08
No, when I try to load a game the actual game appears for a split-second then prompts me to install the missing media,I click on the link. it then tells me that a suitable plug in is not found.Even after reboot.

---

### Post by NoVista on 2008-02-08
candystand.com  works fine here.
mlb.com does too.

But now Yahoo video news player does not.
Ok, two days ago, we had an update on Flash, and it broke it on Gutsy.
So the way I fixed that was I uninstalled non-free flash via Synaptic.
Then I went to youtube, and I let it install it from there. All was fine.

But now today we had another Flash update and it appears it broke it in some way.
Anyone else? Is it just Yahoo video news down, (it's all blank below the video window in the player), or is Flash broken again?

---

### Post by gandaran on 2008-02-08
> **philinux said:**
> I tried it and it works fine. The OP also has java installed and its the same as mine, so to is the flash plugin. Lets hope a reboot sorts it. :)

what did you try the web page or a game, when I try a game it's asks for a flash plugin and my flash work very well, these games only work on windows!

---

### Post by jan quark on 2008-02-08
I installed the update today and everything is fine
so it cannot be completely broken

try to remove it completely as I have suggested above 
or doesn't that help either?

---

### Post by rachel10123@msn.com on 2008-02-08
It doesnt I suppose that i'll have to go along without it.

---

### Post by kennster on 2008-02-08
> **jan quark said:**
> run this in terminal

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

did that and it fixed my problem :D ty

---

### Post by philinux on 2008-02-08
> **gandaran said:**
> what did you try the web page or a game, when I try a game it's asks for a flash plugin and my flash work very well, these games only work on windows!

LOL I must have picked one that works. 

[http://www.candystand.com/uk/play.do?id=18000](http://www.candystand.com/uk/play.do?id=18000)

Some others dont. Weird.

---

### Post by jan quark on 2008-02-08
good to hear kennster 
:)

---

### Post by gandaran on 2008-02-08
> **philinux said:**
> LOL I must have picked one that works. 

[http://www.candystand.com/uk/play.do?id=18000](http://www.candystand.com/uk/play.do?id=18000)

Some others dont. Weird.

yes the one you picked also works on my browser.

---

### Post by nynoah on 2008-02-08
Just wondering if you are on 64bit ubuntu or 32bit?

---

### Post by jan quark on 2008-02-08
who me?

---

### Post by nynoah on 2008-02-08
who ever was having the problem.  The solution may be different if you are on 64bit.

---

### Post by jan quark on 2008-02-08
I run 64 bit and the solution I posted above should work

besides I have updated everything also flash twice this week and everything is fine
no problems at all, but this comment won't help anybody so I am silent now...............

---

### Post by nynoah on 2008-02-08
I was just trying to point out for some people the latest version of the flash plugin for 64bit is buggy.  I have gone and used the older version of the 64bit flash plugin.  This thread explains it and the solution.   [http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash]("http://ubuntuforums.org/showthread.php?t=476924&highlight=64bit+flash")

Noah

---

### Post by ndrone1 on 2008-02-08
> **kennster said:**
> did that and it fixed my problem :D ty

I tried this:
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y

and got this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

and when i try that, i get this:
dpkg: requested operation requires superuser privilege

so i guess i'm asking how to enable supervisor priveleges??

Please keep in mind I am completely new to Ubuntu and Linux all the same. Thanks for your help. Please feel free to PM me if you have the answer I need. I don't know what to do to get my youtube to work!

---

### Post by ubuntu-freak on 2008-02-09
> **ndrone1 said:**
> I tried this:
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y

and got this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

and when i try that, i get this:
dpkg: requested operation requires superuser privilege

so i guess i'm asking how to enable supervisor priveleges??

Please keep in mind I am completely new to Ubuntu and Linux all the same. Thanks for your help. Please feel free to PM me if you have the answer I need. I don't know what to do to get my youtube to work!

 
**sudo dpkg --configure -a**
  
If you're new to Ubuntu you might appreciate my multimedia and video [how-to](http://ubuntuforums.org/showthread.php?t=661833). 
 
Nathan

---

### Post by rachel10123@msn.com on 2008-02-09
Thank you all for your help.:guitar::KS

---

### Post by maniac_X on 2008-02-09
That Hockey game worked for me too but I tried about half a dozen others and none worked so I have no idea.

---

