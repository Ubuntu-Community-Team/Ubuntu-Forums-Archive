---
title: "[PPC] problems with ati display and syncmaster 906bw monitor"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by skier354 on 2008-04-27
Ok, I am trying to get up and running with ubuntu still. Everything is installed but when I boot up I get a messed up screen (half black, half grey, with black squares everywhere). I have searched many forums looking at different xorg.conf's regarding both my ati radeon x800 xt and SyncMaster 906bw. This is what I have for my xorg.conf as of right now, I have tried a few different things in the configuration. My question is, where is the problem? Is it with my ati card, or with my monitor? or both? Any suggestions for fixing this?
System info:
Powermac G5 dual 2 GHz (model identifier: PowerMac7,2)
ati radeon x800 xt video card 256mb w/dvi
1.5 gb ram
160 gb sata hard drive(osx and ubuntu)
320 gb sata hard drive(no os, only for file storage)
Samsung SyncMaster 906bw monitor (1440x900)

Here are all relevant (I think) parts of my xorg.conf
```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Disable "int10"
#	Load	"int10"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R420 JH [Radeon X800]"
	Driver		"ati"
#	Driver		"fbdev"
	BusID		"PCI:240:16:0"
	Option          "NoInt10"       	"yes"
#	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"4"
	Option		"AGPFastWrite"		"1"
#	Option		"UseInternalAGPGART" 	"no"
	Option 		"UseInternalAGPGART" 	"yes"
	Option		"AccelMethod"		"XAA"
	Option		"EnablePageFlip"	"1"
	Option		"AccelDFS"		"0"
	Option          "RenderAccel" 		"on"
#	Option		"GARTSize"		"64"
#	Option		"GARTSize"		"32"
	Option		"ColorTiling"		"1"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option          "MergedXinerama" 	"true"
	Option          "DRI" 			"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
	Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	Displaysize 410 256
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JH [Radeon X800]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900_60"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900_60"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900_60"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900_60"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_60"
	EndSubSection
	SubSection "Display"
		Depth		24 
		Modes		"1440x900_70.00" "1440x900_60.00"
	EndSubSection
EndSection


Section "DRI"
	Mode	0666
EndSection


```

[[IMG]http://img84.imageshack.us/img84/5465/cimg1722wn1.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=cimg1722wn1.jpg)
this image is slightly outdated, now I get a few colored squares near the bottom of the screen, but essentially this is what it looks like

EDIT: sorry I forgot to mention, I am trying to run 8.04. I installed using alternate CD and everything went well until I tried to boot up

---

### Post by stream303 on 2008-04-28
Ok, let's try this.  Do you get anything when you specify this at the second-stage boot: prompt?

```
Linux nosplash video=radeonfb:1440x900-24@60
```

Thanks to BladeMelbourne and OswaldKelso for helping out with this earlier in the archives!

You can see that it specifies your native resolution at 24bit at 60hz refresh.

I would try this at the second-stage boot: prompt, and with both your original Hardy /etc/X11/xorg.conf, and that new one you have.

---

### Post by skier354 on 2008-04-28
thanks for all your help stream303, I really appreciate it. I tried that and the same exact thing happened as with just hitting enter at the second stage boot, and the same as "Linux video=ofonly". I'm wondering, is it my ati card that is giving me issues or my monitor? I was looking at [THIS]("http://ubuntuforums.org/showthread.php?t=726697") thread and noticed that he got ubuntu up and running easily. However he has an Nvidia card. But I saw this in a post and was wondering if this has anything to do with video.
> was able to install Ubuntu 8.04 Hardy
with no issues what so ever (aside from editing the /etc/modules file to load the snd_powermac)


---

### Post by stream303 on 2008-04-28
Ah, I forgot if you are using a dvi or vga connector? (or the vga adapter?)  I looked here and it seems that if you are using analog vga, 1440x900 is not supported by that card:

[http://ati.amd.com/products/radeonx800/radeonX800xtme/specs.html](http://ati.amd.com/products/radeonx800/radeonX800xtme/specs.html)

Can you use any of the other resolutions?  Or perhaps instead of using "autodectect" on the monitor, force the monitor into a resolution directly?  Is there a way to force it into 1440x900?

Oh, the snd_powermac has to do with sound and not video..

---

### Post by skier354 on 2008-04-28
I am using dvi, so it should work just fine (it works without a problem on mac os x at least). Hmmm, I'm not sure if I can force it, I'll check that out and see if I can get that working. I'm kinda confused though about what exactly is wrong here. I get a cursor and it works just fine and I can move it around and it doesn't go past the edges of my screen, its just everything else that is weird graphically. Does that mean the resolution is right? When I move the cursor over where you type your login info, it does change into the insert cursor. I would think that if something were wrong with refresh rate, resolution, ect.. it would affect everything on the screen, but how it is now, the cursor is unaffected.

---

### Post by stream303 on 2008-04-28
Ok, sometimes the gdm display can have strange resolutions, which is where we are sitting at now.

Can you add -Virtual- to this section and try.  I'd also delete any other display subsections other than 24 at this point...

```
SubSection "Display"
                Depth		24
                **Virtual 1440 900**
		Modes		"1440x900_70.00" "1440x900_60.00"
	EndSubSection
```

This has been known to help out strange login resolutions, might be worth a shot..

---

### Post by skier354 on 2008-04-28
Ok awesome, I'll try that once I get a chance (its finals week so i'm a little busy). Also, is there a boot parameter that will let me use a command line? I find it easier that having to boot into a rescue, no big deal though.

---

### Post by stream303 on 2008-04-28
Can you bring up a virtual terminal via CTRL-ALT-F1

(You may have to hit return once to get to the username and password prompt).  It may not look pretty, but should be a lot easier.

To get back to the gui when you are done, just hit CTRL-ALT-F7, however you'll still have a messed up display.  You could restart the xserver, but I'll chicken out and just say that after editing, reboot with

```
sudo shutdown -r now
```

It's not elegant I know... :)

---

### Post by skier354 on 2008-04-29
I edited the xorg.conf and added " Virtual 1440 900" and got rid of everything except 24 depth. It did change what the screen looks like but its still garbage. Also when I hit CTRL-ALT-F1, the display doesn't change, all that happens is my cursor disappears. Hmmmm. I searched and found these two threads. I'm gonna go through and try some of this.
[http://www.backports.ubuntuforums.org/showthread.php?t=280683&page=3]("http://www.backports.ubuntuforums.org/showthread.php?t=280683&page=3")
[http://ubuntuforums.org/showthread.php?t=370204]("http://ubuntuforums.org/showthread.php?t=370204")

---

### Post by stream303 on 2008-04-29
Wow, ok no console either.  Man, scratching my head over this one too...

Have you tried zapping your pram?
[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

Also, I'd be interested to see if we can get some sort of console working to make life easier.  Does this do anything:

1- CTRL-ALT-F1 to get to the console (even though it is dark and you'll be typing in the blind)

2- Hit return

3- Type in your username (in the blind) and hit return.

4- Type in your password and hit return

5- Type
```
setupcon
```

Does this bring the display to life?

---

### Post by skier354 on 2008-04-30
zapping the pram didn't do anything, and I was not able to get to the console using that method. I changed some stuff around in my xorg.conf and now something fails in the startup and I am able to login and use Ubuntu in command line. It says
```

bogl_init failed: EXPLODE

```
and
```

screen init failed

```
when ubuntu starts up as a command line.

Here are applicable parts of my current xorg.conf
```

Section "Module"
#	Load	"i2c"
#	Load	"bitmap"
#	Load	"ddc"
#	Load	"dri"
#	Load	"extmod"
#	Load	"freetype"
#	Load	"glx"
	Disable "int10"
#	Load	"int10"
#	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R420 JH [Radeon X800]"
	Driver		"ati"
#	Driver		"radeon"
#	Driver		"fbdev"
	BusID		"PCI:240:16:0"
	Option          "NoInt10"       	"yes"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
	Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 932 -HSync +Vsync
	Displaysize 410 256
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JH [Radeon X800]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Virtual 1440 900
		Modes		"1440x900_60.00"
	EndSubSection
EndSection
```
I tried to comment out all the extra things that people used to try and get 3d acceleration.

and here is my xorg log file
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux a00957898.dorms.usu.edu 2.6.24-16-powerpc64-smp #1 SMP Thu Apr 10 13:55:52 UTC 2008 ppc64
Build Date: 15 April 2008  07:53:08PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 29 21:28:19 2008
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 101 of section Monitor in file /etc/X11/xorg.conf
	ModeLine VTotal expected
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor


```

It says in the log that there is a parse error on line 101 of section monitor, which is the "Modeline" line. I don't see what is wrong with this as it worked in [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=370204")  thread (post #6). 
EDIT: I commented out the "Modeline" line and it booted up with the graphical error.
Then it also says near the end that there were no screens found. I also tried running 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and
```
sudo dpkg-reconfigure xserver-xorg
```
Both created just a pretty much empty xorg.conf with the same graphical problems (does not start as command line ubuntu).

---

### Post by stream303 on 2008-04-30
Yep, those old standby's of dpkg-reconfigure just don't cut it anymore in Hardy.

At any rate, that INT10 thing made me think about using

Option "BusType" "PCI"

instead of using the standard BusID line.

Check this out from our friends at Genesi for a possible solution:

[http://www.powerdeveloper.org/forums/viewtopic.php?t=1313&postdays=0&postorder=asc&start=0](http://www.powerdeveloper.org/forums/viewtopic.php?t=1313&postdays=0&postorder=asc&start=0)

I admire your willingness to hang in there and experiment - I might have thrown it out the window by now... :)

---

### Post by skier354 on 2008-04-30
Ok thanks a ton for your help! Haha I think I am about to throw it out the window. I'll mess around with it and try some different things and see if I can get something, anything working. It's interesting cause this particular machine was used my microsoft for xbox360 development so it's probably cursed. I'll post anything useful that I find though for any other fellow ppc users with machines as stubborn as mine :D

If anyone looking at this has any epiphanies about what may fix this, don't hesitate to post.

---

### Post by jrkilroy on 2008-05-18
> **skier354 said:**
>  [PPC] problems with ati display and syncmaster 906bw monitor
Ok, I am trying to get up and running with ubuntu still. Everything is installed but when I boot up I get a messed up screen (half black, half grey, with black squares everywhere). I have searched many forums looking at different xorg.conf's regarding both my ati radeon x800 xt and SyncMaster 906bw. This is what I have for my xorg.conf as of right now, I have tried a few different things in the configuration. My question is, where is the problem? Is it with my ati card, or with my monitor? or both? Any suggestions for fixing this?
System info:
Powermac G5 dual 2 GHz (model identifier: PowerMac7,2)
ati radeon x800 xt video card 256mb w/dvi

Did anything come of this?  I'm having the exact same issue (g5 2Ghz ATI Syncmaster 226bw)

---

### Post by skier354 on 2008-05-19
Unfortunately no, I believe the problem is with the x800 xt video card (If that is what you have). I was able to get slackintosh up and running though with some video problems that I haven't yet worked out. I have another forum that has more info as well
[http://ubuntuforums.org/showthread.php?t=690969]("http://ubuntuforums.org/showthread.php?t=690969")
If you learn anything new feel free to post it!

---

### Post by stream303 on 2008-05-20
I wonder if you could run the video driver from Gutsy, while still using the xserver from hardy?

I did this once when I was running Gutsy and used a driver from Feisty, pinned it so it wouldn't get updated, and that worked.

However I have a feeling that the drivers between Gutsy and Hardy might be too different to work - but who knows?

---

### Post by stream303 on 2008-06-14
Just a heads up about the Radeon X800 card - looks like the YDL guys have reported that it is non-functional, so unless something changes, we might be banging our heads against the wall here...

---

### Post by skier354 on 2008-06-14
Oh really? Thats too bad :( I guess I'll have to wait to get my linux

---

### Post by oswaldkelso on 2008-06-15
This may help

[http://forums.debian.net/viewtopic.php?t=26577](http://forums.debian.net/viewtopic.php?t=26577)

---

### Post by stream303 on 2008-06-15
Aha!  Choking on "standard" modelines.  Definitely worth a shot.  Great stuff, and who would have thought to change that modeline to something a bit unique....

---

### Post by oswaldkelso on 2008-06-15
The joys of Xorg 7.3 :) It is funny that my external monitor is a syncmaster (710m) and works fine, but my built in display is still offset. Still good has come from my misfortune, The debian dev that showed me the fix will write a the new driver that will  automatically work and so will the mini vga. Very cool.

Edit: I show say partial fix.

---

