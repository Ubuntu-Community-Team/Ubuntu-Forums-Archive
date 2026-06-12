---
title: "Java Virtual Machine - won't run java apps in browser"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Her Ghost on 2007-08-26
Hi, 

****SOLUTION AT FOOT OF POST - THANKS jw5801****

I've been struggling to get java working properly on my system.  I have the following packages installed through Adept:

Java 1.4 plugin for mozilla/firefox
Java Web start 1.4
Sun Java 5.0 Runtime
Sun Java 6 web start
Sun Java 6 web start (32bit)
Java 1.4 (Blackdown Java 1.4)
Sun Java 6 Runtime
Sun Jave 6 Runtime (32 bit)
(Ubuntu restricted extras)
Sun Java 5.0 Console
Sun Java 6 Console

When I try to run a java app in my browser (firefox), for example[ this page]("http://java.com/en/download/help/testvm.xml") I just get the application red-X after a few seconds.

The info from the Java Console is as follows (sadly I'm not a programmer so I can't tell if it's something really easy or not!):

```

Java(TM) Plug-in: Version 1.4.2
Using JRE version 1.4.2-02 Java HotSpot(TM) 64-Bit Server VM
User home directory = /home/leigh
Proxy Configuration: Browser Proxy Configuration


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------
java.lang.UnsupportedClassVersionError: testvmVersions (Unsupported major.minor version 49.0)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:157)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:123)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:561)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:619)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1879)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:548)
	at sun.applet.AppletPanel.run(AppletPanel.java:299)
	at java.lang.Thread.run(Thread.java:534)

```

I don't know whether it is related or not, but I am also having problems running a standalone java app called Cityware (you may have seen it through facebook).

The error that I get with that (which may be totally unrelated) is:

```

Exception in thread "main" java.lang.UnsatisfiedLinkError: no avetanaBT in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1517)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at de.avetana.bluetooth.util.LibLoader.loadLib(LibLoader.java:150)
        at de.avetana.bluetooth.util.LibLoader.loadBTLib(LibLoader.java:48)
        at de.avetana.bluetooth.stack.AvetanaBTStack.<init>(AvetanaBTStack.java:58)
        at de.avetana.bluetooth.stack.AvetanaBTStack.<init>(AvetanaBTStack.java:52)
        at de.avetana.bluetooth.stack.BluetoothStack.getBluetoothStack(BluetoothStack.java:94)
        at javax.bluetooth.LocalDevice.<init>(LocalDevice.java:60)
        at javax.bluetooth.LocalDevice.getLocalDevice(LocalDevice.java:73)
        at Cityware.<init>(Cityware.java:44)
        at Cityware.main(Cityware.java:33)

```

(Note that I'm not particularly asking for support with this second app here, unless it's directly related to my browser issue.  :)

Thanks for any help

Leigh


**SOLUTION**

There isn't a 64-bit sun java plugin.  Using the plugins below gets around the problem.

```

sudo apt-get install java-gcj-compat java-gcj-compat-plugin gcjwebplugin-4.1

```

---

### Post by por100pre1 on 2007-08-26
Try removing all that stuff and install only this:

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Her Ghost on 2007-08-26
thanks for your help.  after removing everything else and running the command above, there is one error message:

```
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

could this be related to my using 64bit kubuntu?

---

### Post by por100pre1 on 2007-08-26
Oh, sorry. Install this too:

```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by Her Ghost on 2007-08-26
yeah, got that, but still can't get anything working in the browser.

now I get an 'install missging plugins' button that refers me to the sun website.

I installed the files as they suggested, but the most recent package doesn't appear to contain a /plugins directory so I can't create a link to it in the firefox folder

any ideas?  am I missing something obvious?

---

### Post by por100pre1 on 2007-08-26
> **Her Ghost said:**
> yeah, got that, but still can't get anything working in the browser.

now I get an 'install missging plugins' button that refers me to the sun website.

I installed the files as they suggested, but the most recent package doesn't appear to contain a /plugins directory so I can't create a link to it in the firefox folder

any ideas?  am I missing something obvious?

The 'install missging plugins' button means the plugin is missing. Type this in the webpage address bar in Firefox: **about: plugins** *without the space after **:*** then click go. Post the results.

---

### Post by Her Ghost on 2007-08-26
```

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

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
audio/x-scpls 	Shoutcast Playlist 	pls 	Yes

```

no mention of java in there.

when I followed the install missing plugins link, I downloaded and installed the file that was linked to from the sun website.  the installation was fine, but had no effect.  further reading suggested making symbolic links to the plugin in the firefox directory.  unfortunately the file linked from sun doesn't have the files that its instructions refer to!

---

### Post by por100pre1 on 2007-08-26
Let's try to do it another way. Look to uncheck and check back again Ubuntu Restricted Extras in Add/Remove... or try this:

```
sudo aptitude reinstall ubuntu-restricted-extras
```

I don't get to see what's going on... :-k

---

### Post by Her Ghost on 2007-08-26
reinstall ran ok, but still no java.... :(

---

### Post by Her Ghost on 2007-08-26
I just reinstalled the Java 1.4 plugin for Moxilla/Firefox, and this adds the libjavaplugin_oji.so file to the firefox plugins folder, like the manual java install was supposed to do.  but now I just get the red-x on the java app with this error message again:

```

java.lang.UnsupportedClassVersionError: testvmVersions (Unsupported major.minor version 49.0)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:157)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:123)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:561)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:619)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1879)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:548)
	at sun.applet.AppletPanel.run(AppletPanel.java:299)
	at java.lang.Thread.run(Thread.java:534)

```

and my about:plugins now contains all this:

```

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


```

---

### Post by Her Ghost on 2007-08-26
in case any night hax0rs can help :D

---

### Post by jw5801 on 2007-08-26
There isn't a 64-bit sun java plugin. Try using:
```
sudo apt-get install java-gcj-compat java-gcj-compat-plugin gcjwebplugin-4.1
```
Which is a third-party 64-bit java engine with plugin. From blackdown java I think. It works reasonably well though does give some strange results very occasionally.

---

### Post by Her Ghost on 2007-08-26
Thank you - that has solved my problem.

I didn't know that there wasn't a 64bit version available, but the packages you suggested work fine.

Thanks for your help.

---

### Post by jw5801 on 2007-08-27
Not a prob! It took me quite a while to find out that was why I couldn't do it. So I'm happy to point people in the right direction. Java is one of the few things that lack in 64-bit to date, hopefully this will change now Sun's code is open source.

---

### Post by stroudcuster on 2007-08-31
The problem is that Sun considers 64 bit a server, rather than a client platform.  The amd64 SDK and JRE downloads do not include Java WebStart (javaws) or the plugin.  Given that at least half of the PCs on display in the typical retail outlet are 64bit, it's a bit overdue for Sun to reconsider this position.

I'm also having difficulty getting a working flash player plugin for the 64 bit platform.

---

### Post by jw5801 on 2007-09-01
Check out Kilz nspluginwrapper script, it worked for me, I'll find the link and post it back here.

[EDIT](http://ubuntuforums.org/showthread.php?t=476924)

---

