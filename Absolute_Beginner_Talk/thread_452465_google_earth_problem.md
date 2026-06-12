---
title: "google earth problem"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-05-23
when i start google earth , it crashes with following message.> ejaz@ejaz-desktop:~$ googleearth
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x1ec) [0x8057aa4]
  ./googleearth-bin [0x8057e8b]
  [0xffffe420]
  ./libbase.so(_ZN5earth12MemoryWindow17ShowMemoryMessageEP7QWidget7QStringbS3_S3_RKS3_S5_S5_+0x36b) [0xb7f56cbf]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl18requireDXOGLSwitchERK7QStringS4_+0xf25) [0xb36f74fd]
  ./librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0x26c) [0xb63a1e74]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x64) [0xb638f02a]
  ./libgoogleearth.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x51) [0xb7788fbf]
  ./libqt-mt.so.3(_ZN7QWidget5eventEP6QEvent+0x277) [0xb6e9fa17]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xb6df2fc1]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xc9) [0xb6df3aa9]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x266) [0xb6e9e976]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6e9e6cb]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6e9e917]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6e9e6cb]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6e9e917]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6e9e6cb]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6e9e917]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6e9e6cb]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6e9e917]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6e9e6cb]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6e9e917]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6e9e6cb]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6e9e917]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0xb6e9e6cb]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0xb6e9e917]
  ./libqt-mt.so.3(_ZN11QMainWindow4showEv+0x93) [0xb6f72b53]
  ./libqt-mt.so.3(_ZN7QWidget10showNormalEv+0x33) [0xb6e97fe3]
  ./libgoogleearth.so(_ZN10MainWindow18readScreensizeInfoEv+0x550) [0xb775db0a]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEiPPc+0xce9) [0xb7776aa1]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationC1EiPPcb+0xf76) [0xb7777f0c]
  ./googleearth-bin(main+0x123) [0x805830d]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb615cebc]
  ./googleearth-bin(__gxx_personality_v0+0x79) [0x8057931]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/ejaz/.googleearth/crashlogs/crashlog-C5C581B2.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

ejaz@ejaz-desktop:~$


can anybody help me?

---

### Post by Flump5000 on 2007-05-23
just try reinstalling it.

---

### Post by u04f061 on 2007-05-24
> **Flump5000 said:**
> just try reinstalling it.

is this a common problem?

---

### Post by speedygeo on 2007-05-27
The Automatix wiki write that Googleearth don't works on debian-based distro when we use an ATI graphics card!!!
Sig!:(

---

### Post by swisscow on 2007-05-27
That's nonsense. I have an ATI  X300 and googleearth works sweet. I just have to use the fglrx drivers - though I can't seem to get Beryl working adequately with them. However, google earth is so cool, I'd rather use that anyday.

---

### Post by u04f061 on 2007-05-28
i don't hava any ati driver

---

### Post by swisscow on 2007-05-29
I think, you can add through the restricted drivers in Feisty, not so sure because I use Kubuntu, and it doesn't seem so clear as in Gnome (though to be honest I haven't looked that hard).

There are lots of threads about installing the fglrx drivers on these forums, though to be fair some people seem to have more success than others.

---

### Post by SoulinEther on 2007-05-29
That's not true... I am running the **radeon** drivers for my 9200... can use Google Earth, Beryl, Beryl + Google Earth no problem.

(That last one shocked me, I opened it up to test it and it ran very smoothly!) There is hope for you too.

---

### Post by swisscow on 2007-05-29
Good for you - I have had no luck, but I don't think (or know) that the graphics card in my laptop is as well supported.

I have achieved: Google Earth with fglrx, Google Earth freezing at start up with ati drivers, no luck installing aiglx and google earth working but sooo slowly with xgl.

It does seem a bit hit and miss with Beryl and Google Earth and ATI  from the many hours I have read, but as I said earlier, I would rather have Google Earth working ( I live near the Alps and it's great for planning walking - or looking at the walks when it's raining :(  )

---

### Post by SoulinEther on 2007-05-29
Wow forget about Beryl, that sounds AWESOME! :D

Did you install Google Earth through Google's download or through like Automatix?

---

### Post by swisscow on 2007-05-29
Downloaded it from google earth website. I was going to use automatix but I found it much easier to do it myself, and as I'm running Kubuntu, installing automatix puts a hell of a lot of stuff on in the background which I don't really want / need.

As for Google Earth, the detail of a lot of the Alps is so good you can see many of the footpaths! Also tilting the view gives a fantastic view of some of the ridges - have a look at the north face of the Eiger

---

### Post by arnieboy on 2007-05-29
> **speedygeo said:**
> The Automatix wiki write that Googleearth don't works on debian-based distro when we use an ATI graphics card!!!
Sig!:(
where did we say that?

---

### Post by u04f061 on 2007-05-29
> Did you install Google Earth through Google's download or through like Automatix?

I installed from medibuntu

Why do i need ati etc drivers .I am also using kubuntu. I run googleearth on windows xp without any problem. I think i should do some sticky thing to get out of this hell. I am feeling same problem with qt-designer. please see [http://ubuntuforums.org/showthread.php?t=456294]("http://ubuntuforums.org/showthread.php?t=456294")

---

### Post by swisscow on 2007-05-30
Ok, here's what I did - hope it helps

Installed Kubuntu
Followed the sticky at the top of the absolute beginners forum : installing ubuntu 7.04 ATI X*** cards
Edited my xorg.conf (this may not be necessary but I had to)

first make a backup of your current xorg.conf just in case...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bup
```

Then I edited my xorg.conf using:

```
kdesu kate /etc/X11/xorg.conf
```
 so it looked like this
```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

[COLOR="Red"]Section "Device"
	Identifier	"ATI Technologies Inc M22 [Radeon Mobility M300]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection[/COLOR]

[COLOR="Red"]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
         Option 	"Composite"   "0"
EndSection
```[/COLOR]

The important bits are in red. Obviously your device names may be different

I then logged out, restarted xserver (rebooting works).

If all is well, go to the google earth website, download and install using

```
sudo sh GoogleEarthLinux.bin
```

from the folder you put the download in

If all is not well and you can't log in:  from the command line do
```

sudo cp /etc/X11/xorg.conf.bup /etc/X11/xorg.conf
```

and reboot and you should be back where you started

Good luck!!

---

### Post by Brian96 on 2007-06-18
> **u04f061 said:**
> when i start google earth , it crashes with following message.

can anybody help me?

I get the same error. I am running Feisty Fawn with an ATI Radeon X300 with proprietary drivers and a dual-head setup. I have tried installing and uninstalling using a wget script I found on here somewhere, as well as through the medibuntu repositories. Same error each time.

My xorg.conf is configured similarly to swisscow's, except that mine has additional entries for the second monitor.

Any suggestions?

---

### Post by mwacky on 2007-06-25
Google Earth works great on a ATI Radeon Xpress 200M for me, only problem is when I suspend my laptop by closing the lid, Google Earth will hang, not use any cpu or give any messages in console.  So I just have to reboot.  Annoying problem I can't find an answer for: 
[URL="http://ubuntuforums.org/showthread.php?t=451960"]
http://ubuntuforums.org/showthread.php?t=451960[/URL]

Try Envy for easy graphics card setup...

---

### Post by firmwire on 2007-07-10
Decided to post this in more than one forum section:

I have been all over the forums and have found some very good info for possibly solving my issue. I am not sure if it will work or not since I am not at home at the moment. I wanted to run some things by you all to make it easier when I do get home.

Issue: 
Running Compiz Fusion ( perfectly) in xgl w/ gnome. I have fglrx as the driver I am using. I have Composite set to "0" and have even changed it to "false".
When I run glxinfo I get direct rendering is NO. 
glxgears works fine in any session I do.
From what I can find, in order for compiz fusion to run it has to be in xgl mode. But google earth NEEDS direct rendering ( I think).
I think if I just go into a non xgl session the same glxinfo gives me YES for direct rendering. I don't remember though at the moment.
Even so...when I run google earth in any session I get 100% CPU usage from it. It just hangs at the initialization splash screen. I can still kill the process, so it doesn't lock my system up completely. 
I have read that people have been able to get it to work with Beryl and ATI cards running together. I am just trying to figure out how to get it to run with my setup.

In case the question comes up, I have installed it two different ways. I had installed it through Automatix. Then uninstalled it. Then I installed it from the download from the google earth linux download site. Both installs went fine. Both hang and produce 100% cpu usage when activated and hangs on the splash screen.

I found this post [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636). Do you think this will solve my problem?

Also I have seen posts about libGL.so.1.bz2 and libGL.so.1.tar.bz2, and I do you think this may fix my issue?

Oh yeah... and I even tried this earlier today: DISPLAY=:0 /usr/local/google-earth/googleearth. It just loads the splash screen and hangs.

I know people have had the issue with 100% cpu usage, but I couldn't find anything saying what they did to fix it or if they were even able to.
I have seen in one place that one person actually installed an extra stick of RAM and that helped. But I don't think I should have to. Everything else works great. I only have 1GB on this system currently.

I am running Feisty 64 and it runs completely stable. I love it!

Any suggestions/solutions are greatly appreciated. Thanks in advance.

---

### Post by firmwire on 2007-07-11
/bump

---

