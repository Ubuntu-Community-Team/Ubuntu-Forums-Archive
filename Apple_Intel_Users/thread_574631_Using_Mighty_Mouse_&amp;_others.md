---
title: "Using Mighty Mouse &amp; others"
date: 2007-10-13
forum: Apple Intel Users
---

### Post by Loki1989 on 2007-10-13
I though It would get a post started showing what got everything running smoothly for myself on my Macbook intel. There is wireless blue tooth and to get the AWN dock bar.


Wireless installs:

Install Build Essentials
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r)
```

Go to madwifi.org to download he latest the old trunk code install didn't work after my drivers wiped
after extract them to the desktop and cd into the folder by dragging it into the terminal

type ls into it and you should get

```
ath            contrib    include          Makefile.inc  regression  tools
ath_hal        COPYRIGHT  INSTALL          net80211      release.h
ath_rate       docs       kernelversion.c  patches       scripts
BuildCaps.inc  hal        Makefile         README        THANKS
```

To install
```
make
sudo make install
```
Answer r to the question it asks
Restart to have it ready

Blue tooth for mice and others:
Go into synaptic and search for
gnome-bluetooth and install it

then 

```
 sudo hidd --search
sudo hidd --connect aa:bb:cc:dd:ee:ff

```

For bluetooth at startup
```
 sudo cp /etc/default/bluetooth /etc/default/bluetooth_backup
  sudo gedit /etc/default/bluetooth
```

Change
```
HIDD_ENABLED=0
```
to
```
HIDD_ENABLED=1
```

and change

```
 HIDD_OPTIONS="--master --server"
```
to
```
 HIDD_OPTIONS="--connect aa:bb:cc:dd:ee:ff --server"
```
add more hidd options for more items all on the same line

Avant Window Navigator:

```
sudo apt-get install build-essential automake1.9 autotools-dev bzr libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev
```
and more
```
bzr co http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator
```
and finally to install
```
   3. cd avant-window-navigator/
      ./autogen.sh
      make
      sudo make install
```
For applets
```
# sudo apt-get install libgnome-menu-dev librsvg2-dev libgtop2-dev
bzr co http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk awn-extras
   3. cd awn-extras/awn-applets/awn-core-applets/
      ./autogen.sh
      make
      sudo make install
```
Run Avant in Applications> Accessories> Avant Window Navigator

also go onto synaptic and get compizconfig-settings-manager for a great way to configure fusion.

These were pulled form many posts and sites and feel free to add more stuff later down the line I would like to hear of others experiences and see how I can help.

---

### Post by dmber on 2007-10-14
is this for gutsy or feisty?

---

### Post by Loki1989 on 2007-10-14
These were all working on my gutsy install so I would go with gutsy and update everything first update wipes wireless drivers. but shouldn't the drivers for the wireless work in all recent versions of ubuntu.

---

### Post by cyberdork33 on 2007-10-15
> **Loki1989 said:**
> These were all working on my gutsy install so I would go with gutsy and update everything first update wipes wireless drivers. but shouldn't the drivers for the wireless work in all recent versions of ubuntu.
People were having issues with some of the latest madwifi drivers in feisty.

---

### Post by Loki1989 on 2007-10-16
> **cyberdork33 said:**
> People were having issues with some of the latest madwifi drivers in feisty.

I haven't seen any of those but in the last weekend I have posted more on here than I have in a long time so as of late my macbook has become my main computer experience.

---

### Post by cyberdork33 on 2007-10-16
> **Loki1989 said:**
> I haven't seen any of those but in the last weekend I have posted more on here than I have in a long time so as of late my macbook has become my main computer experience.
There are quite a few. The 2695 version was the only one that would work for people for a long time. I don't know if that has changed any.

Also there is a bluetooth how to in the stickied FAQ, Just FYI.

---

### Post by OshKoshPoshJosh on 2007-10-18
Using this method, Gutsy will recognize my wireless mighty mouse. I can move the mouse around just fine, but for some odd reason, I cannot click. I will left or right click, but Ubuntu simply does not register the click of the mouse.

Any suggestions would be appreciated.

Thanks for this guide, by the way.

---

### Post by OshKoshPoshJosh on 2007-10-20
Oddly enough, I had to reinstall Ubuntu Gutsy for other reasons, but the mouse is now working fully.

A bit odd, but it worked.

---

### Post by billy420 on 2007-11-01
would this work for the new apple wireless keyboard too?

---

### Post by jslmg on 2007-11-09
I'm running an Intel Mac mini with Ubuntu 7.10, latest kernel, on a 10GB partition. I've got Compiz fully installed, and I've been using it with great success, full desktop effects. 

After working for several hours, I had limited success with Loki1989's codes and configs for Mighty Mouse and the Apple wireless keyboard. I had both working briefly, including all mouse key bindings. However, the first thing I noticed was that Ubuntu could not hold the connection to these bluetooth devices. The connection kept dropping out, then I had to reconnect in the terminal using the hidd --search command.

But that weak connection was the least of my problems. It appears that whatever I did while making the changes Loki1989 recommended, as well as the mouse-key binding changes to the /etc/X11/xorg.conf, have broken my desktop.

After making those changes, and then trying to get the bluetooth to hold its connection to the wireless mouse and keyboard, I decided it would be a good idea to restart the computer.

But when I restarted, I first saw that Linux was repeating attempts to start LIRC. After it tried several times, it opened in "low graphics mode," saying it was unable to detect my graphics card or monitor type. I was unable to make any settings manually.

So, I first turned off both my wireless mouse and wireless keyboard, then I restarted the computer again.

After that second restart, Ubuntu booted into full graphics mode. I had to make an "auto adjust" to my monitor to align the GUI when the login screen came up, but the screen was in normal resolution. 

When the desktop was loaded, there were not desktop effects--no desktop switching, no cube, nothing. Windows are very jerky and uneven when I drag them, though all other graphics seem normal. The panel workspace switcher had only one square, indicating that compiz was not running at all. 

I opened CCSM fine, but I noticed that all my previous settings were still there. I began trying different things at GUI level--I tried enabling GL Desktop, which was unstable. The "Enable GL Desktop" box would not stay checked; when I closed the GL Desktop settings, then reopened them, the box was unchecked again. 

It appears that everything is basically normal in the Ubuntu desktop; it's just that it's all default Ubuntu, no compiz/beryl/GL at all. No AWN, either.

How do I get compiz back?:sad:

I've resigned myself to not having wireless mouse or keyboard, until or unless someone comes up with a stable solution for that. But I want my compiz back! I worked many hours to get that set up too!

Any help? I've offered as much detail as I can muster right now; if someone can tell me where and what to look for, I'll provide any info I can.

thanks!

---

### Post by cyberdork33 on 2007-11-09
you changed the video driver you are using somehow. post you xorg.conf.

---

### Post by jslmg on 2007-11-09
OK, thanks. I was wondering about that, because I did have to change the xorg.conf to get Mighty Mouse to work--all according to one of the threads in this forum.

BTW, I did try compiz --replace, and I got this output:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

But I DO have Xgl installed.

Back to the xorg.conf: There are two. The current xorg.conf is identical to  the xorg.conf.failsafe, which I presume was generated for that "low graphics" mode??? The second is xorg.conf.1. Is that the original conf file?

I'm posting both here. First, the current xorg.conf:

> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

Here's the xorg.conf.1 file:

> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Option "CorePointer"
	Driver "evdev"
	Option "Name" "Mitsumi Electric Apple Optical USB Mouse"
	Option "HWHEELRelativeAxisButtons" "7 6"
	Option "Buttons" "8"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"MNT-ANALOG"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"MNT-ANALOG"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by cyberdork33 on 2007-11-09
The xorg.conf.1 is a backup of a config file you had. you can try to cp it back to normal:
```
sudo cp /etc/X11/xorg.conf.1 /etc/X11/xorg.conf
```

Otherwise, you might just start over with a new xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You are currently using the vesa driver which is why performance is bad. You likely want to use the 'Intel' driver.

P.S. you can uninstall XGL, it is not needed for Intel graphics.

---

### Post by jslmg on 2007-11-09
Well, that conf.1 file turned out to be the trouble. After cp'ing it, I restarted, and the computer popped back into low-graphics mode.

The second option you gave worked, and now Compiz is back, as I set it before.

Which Intel driver should I use? Right now it's set to "Intel Experimental Modesetting..." by default.

Though Compiz is running quite fast, windows redraw very slowly as I move them. Scrolling is jerky and tediously slow. Is that a problem with the driver, or is it a setting in Compiz?

---

### Post by cyberdork33 on 2007-11-09
> **jslmg said:**
> Well, that conf.1 file turned out to be the trouble. After cp'ing it, I restarted, and the computer popped back into low-graphics mode.

The second option you gave worked, and now Compiz is back, as I set it before.

Which Intel driver should I use? Right now it's set to "Intel Experimental Modesetting..." by default.

Though Compiz is running quite fast, windows redraw very slowly as I move them. Scrolling is jerky and tediously slow. Is that a problem with the driver, or is it a setting in Compiz?

I haven't seen that experimental thing before. Make sure that the driver line in the device section of your xorg.conf says 'Intel'. and reboot. 

It also might be a video memory issue. What resolution are you trying to use?

---

### Post by jslmg on 2007-11-09
Fickle stuff, this! I checked the xorg.conf, and the driver line did say "Intel." The device is listed in xorg.conf as "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller". But in the Graphics and Screens preferences, it still says "Intel Experimental Modesetting Driver."

 I didn't make any changes, but I rebooted anyway, and now everything is perfect--zippy redrawing (not as smooth as in Mac OS X, but then is it ever?), smooth scrolling.

I'm using 1280 X 1024, 60Hz refresh, on a 19-inch monitor. These are the default settings, aren't they?

Well, I don't know what I did wrong... I still want to get my wireless mouse and keyboard working, but it'll have to wait until another day.

Thanks, Cyberdork!

---

### Post by cyberdork33 on 2007-11-09
> **jslmg said:**
> I'm using 1280 X 1024, 60Hz refresh, on a 19-inch monitor. These are the default settings, aren't they?
Depends on the monitor.

There should be a bluetooth manager icon in the system tray area where you can connect new devices. I quit using my bluetooth keyboard though because it keeps dropping out, in the middle of me typing. It used to work great in Feisty.

---

### Post by jslmg on 2007-11-09
Yeah, as I described in my urgent tome above, that "dropping out" was the problem I had with Bluetooth even after I got it working. I got both devices connected and working, finally, but then they would not stay connected. 

I think the video got screwed up when I was following some instructions on getting the mouse key bindings to work on Mighty Mouse. There was an xorg.conf file that was provided in one of these threads on the Mighty Mouse or wireless mice. I'll see if I can locate  that thread and its xorg.conf and link it here. 

Looks like I'm not gonna get wireless working anytime soon, then. That support is just not ready yet.

---

### Post by cyberdork33 on 2007-11-09
> **jslmg said:**
> Yeah, as I described in my urgent tome above, that "dropping out" was the problem I had with Bluetooth even after I got it working. I got both devices connected and working, finally, but then they would not stay connected. 

I think the video got screwed up when I was following some instructions on getting the mouse key bindings to work on Mighty Mouse. There was an xorg.conf file that was provided in one of these threads on the Mighty Mouse or wireless mice. I'll see if I can locate  that thread and its xorg.conf and link it here. 

Looks like I'm not gonna get wireless working anytime soon, then. That support is just not ready yet.

If you want to use something from another xorg.conf. You just need to make sure to 1. make a backup and 2. only copy the section that you need. i.e. If you are trying to configure the mouse, you only need to copy the mouse section.

I think the bluetooth support in linux is fine, it is just Ubuntu messed something up in this last release, likely in an attempt to make things easier to connect or something. You might check if there is a bug report in launchpad on this if you really want to get it working.

---

### Post by jslmg on 2007-11-09
I just happened to be searching for that post with the xorg.conf file when you sent that last note, cyberdork.

> If you want to use something from another xorg.conf. You just need to make sure to 1. make a backup and 2. only copy the section that you need. i.e. If you are trying to configure the mouse, you only need to copy the mouse section. 

Yes, all that's true, and I did all that--I only copied the the section I needed, cuz that was all that was given in the posting that I used. The posting also gave instructions for how to back up the original. Hang on, I'm looking for that thread now....

---

### Post by jslmg on 2007-11-09
Here's the thread:

[http://ubuntuforums.org/showthread.php?t=223576&highlight=mighty+mouse](http://ubuntuforums.org/showthread.php?t=223576&highlight=mighty+mouse)

I'd like to understand what I did wrong, cuz it looks like the remedy described there is working for others. I may even venture trying it again, now that I know what to do if I screw up my video again.

I suppose it's possible, too, that I messed up the video in some other way, not related to this thread, but I can't think of what that would be.

---

### Post by jslmg on 2007-11-09
Aha! Another user reported that making those changes to xorg.conf "broke" his X server, too!

> **nandotron said:**
> Hi, A little more info:  i have successfully gotten my mighty mouse to work with horizontal scrolling and button 8.  the only problem is that when I restart the computer, X breaks.  here is my original xorg.conf:

I wonder why. Is there a way to avoid that problem, while getting the mighty mouse to work?

Can we somehow merge these threads, if that's a good idea?

---

### Post by cyberdork33 on 2007-11-10
> **jslmg said:**
> Aha! Another user reported that making those changes to xorg.conf "broke" his X server, too!



I wonder why. Is there a way to avoid that problem, while getting the mighty mouse to work?

Can we somehow merge these threads, if that's a good idea?

Might be best to just continue posting in the other thread.

To backup your conf file, just use the cp command.

sudo cp /directory/directory/originalfile /anotherdirectory/anotherdirectory/backupfile

Then if something breaks just copy it back to it's original location. As an example, I would backup my xorg.conf like this:
```
sudo /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If I need to restore it, I copy back the other way:
```
sudo /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by jslmg on 2007-11-10
Thanks, cyberdork. I'll remember that the next time I go doin' risky things with my config files.

:smile:

---

### Post by changuito on 2007-11-16
Hi all. Maybe I'm missing something, but I cant detect my mighty mouse at all in kubuntu. It works fine in OSX, so it is switched on (i've checked it). Below is a transcript of the first step

> 
changuito@toll:~$ sudo hidd --search
[sudo] password for changuito:
Searching ...
        No devices in range or visible



Thanks in advance.

---

### Post by cyberdork33 on 2007-11-16
> **changuito said:**
> Hi all. Maybe I'm missing something, but I cant detect my mighty mouse at all in kubuntu. It works fine in OSX, so it is switched on (i've checked it). Below is a transcript of the first step

Thanks in advance.

Make sure you put it in discoverable mode... switch it off, and then switch it back on just before searching.

---

