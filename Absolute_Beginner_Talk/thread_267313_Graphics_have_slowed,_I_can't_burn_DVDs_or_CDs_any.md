---
title: "Graphics have slowed, I can't burn DVDs or CDs anymore, and one more thing."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-09-28
I don't know how these could be related, but either I just happen to have 3 unrelated problems at once, or they're all part of an interesting syndrome.

About 2 weeks ago, my graphics slowed down in a big way, my DVD+-RW drive stopped being able to burn DVDs and CDs, and some tweaks I installed for Firefox to improve the appearance of buttons and fields stopped working.

Graphically... I use an ATI Radeon 9500.  glxgears went from many thousands of fps to 57 fps and no actual animation displayed, all my 3D apps can now be measured in "seconds per frame" rather than "frames per second" (Google Earth, Enemy Territory, Neverball, etc.). I addition, my 2-D graphics have taken a hit:  even small windows of video playback are terribly slideshow-like, and when I drag across the desktop to select icons, for example, the shaded drag-select box stutters and lags behind me.

As far as DVD and CD burning goes, Totem just hangs when trying to burn.  I select the files, click "burn," and it does nothing.

The Firefox problem may be harder to track down, since it's a little-known modification.  But basically, text fields and buttons look awful to many folks in the standard version of FF in Ubuntu, and this modification introduces replacement buttons and text fields that are much nicer.  It, too, stopped working, and FF reverted to its standard elements.

I can't imagine how all these could be related, but they all happened at the same time, and I don't remember installing anything, or modifying any system config files immediately before.  Actually, I do remember re-running Automatix to get Flash to update properly (which Flash wasn't doing on its own), but that's the only change I asked it to make.

Does any of this ring a bell for anyone?  I do love working (and playing) in Ubuntu, but I feel like I'm walking a tight rope most of the time.  Thanks for any ideas you may be able to contribute!

-Mark

---

### Post by podunk on 2006-09-28
About 2 weeks ago they updated the kernel and this caused problems for some ATI folks with older cards. 

Apparently the drivers supplied to us poor suffering ATI users are crap because ATI is willing to release new drivers to windows every week, but us Linux scummers only get new drivers when the moon is blue.

I bet if you reinstall your drivers the problem will go away.

---

### Post by pay on 2006-09-28
If you updated the kernel you need to re-compile the kernel modules for the driver.

---

### Post by mjpatey on 2006-09-28
Wow, how in the world do I do that?

I just tried reinstalling the driver, but when I do "fglrxinfo", I get:

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

...when it should be listing ATI, not "Mesa", right?

---

### Post by mjpatey on 2006-09-28
Does anyone know what I need to do to get fglrxinfo to show ATI instead of Mesa?  I'm still running really slow.

Looking at xorg.conf, here are some relevant sections, and they show the wrong video card model:

```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200]"
	Monitor    "DELL 1801FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

I'm using a 9500, not a 9200.  This has never happened before, and I'm not sure how to fix it.

Anyone?

---

### Post by podunk on 2006-09-28
<blush!> I ended up reinstalling Ubuntu before it was all over.

I think where I started to go wrong is I didn't save my xorg.conf file. The second thing I did wrong was uninstall the driver and rebooting before installing a new driver. :-D I mean – that's what you do in winDUH's right?

So, you likely don't want to do anything at all like that.

Once I reinstalled I installed the proper headers for my kernel (k7 for me) then followed the howto on this page:
[http://wiki.cchtml.com/index.php/Installation](http://wiki.cchtml.com/index.php/Installation)

Method 1 works for us with older ATI  graphic cards.

I think if I had: 
backed up my /etc/X11/xorg.conf file
then used used the Package Manager to uninstall the fglrx driver
then followed the how to it would have worked

I guess I'll find out the next time they update the kernel :-)

---

### Post by pay on 2006-09-29
[QUOTE=mjpatey;1556598]Wow, how in the world do I do that?
/QUOTE]

```
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

```Should do the trick.

---

### Post by pay on 2006-09-29
> **mjpatey said:**
> Does anyone know what I need to do to get fglrxinfo to show ATI instead of Mesa?
Edit this file```
sudo gedit /etc/default/linux-restricted-modules-common
```change this```
DISABLED_MODULES=""
```to this```
DISABLED_MODULES="fglrx"
```and continue to install the driver.

---

### Post by mjpatey on 2006-09-29
Thanks, everyone!

I followed podunk's advice above, using the Howto link in that post.  Did the trick!  Thanks to everyone who posted.  I'll be bookmarking this post!

-Mark

---

### Post by T_W on 2006-09-29
Hmmm, I see lots of people report driver problems after kernel upgrades. 

I installed the ATI support using the mechanism described in the wiki page [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and I have never had a compatibility problem.  

Usually when a new kernel version is available, a new companion fglrx module comes with it.

---

