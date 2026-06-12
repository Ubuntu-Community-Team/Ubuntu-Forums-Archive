---
title: "lost borders in ubuntu ver 7.10"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Dasigna on 2007-10-03
I would like to restore original theme of ubuntu 7.10. I lost borders when i tried to use visual effects and some icons at the top look different. thank you for  your help.

---

### Post by wil313 on 2007-10-03
In Gusty, they have all the modifications piled in one place, go to system-> Preferences-> and Appearance; You should find everything you need there...

---

### Post by Dasigna on 2007-10-03
i did but it does not work , when i go in appearance menu and I switch visual effect from none to normal or extra borders disappear

---

### Post by asmiller-ke6seh on 2007-10-19
> **Dasigna said:**
> i did but it does not work , when i go in appearance menu and I switch visual effect from none to normal or extra borders disappear

Same, here. When I enable either the **Normal** or **Extra** Visual Effects, I lose the Title Bar on any and all windows (existing or new), and I also lose the ability to drag and drop my applications windows around the screen.

If I turn off Visual Effects, I get my title bars back and my ability to drag and drop applications windows.

When the Title Bars dissapear, so do the windows controls icons (minimize, mazimize, exit).

I use nVidia on my System 76 laptop. I installed the latest System 76 drivers and rebooted my system both before (and after) installing Gusty Gibbon.

--------LATER-----------------------------------------------------------------
I found the answer later in this thread; see message #12.

I did two things to solve this problem, thanks to **dpar** pointing to a blog by Forlong hosted by some great guys in Germany. This is what I love about being an Ubuntista -- It's the Community!!!


FIRST: using the Synaptic Package Manager, I downloaded EMERALD by searching for "emerald" and installing it, then

SECOND: I went to **System -> Preferences -> Appearance** and I selected the **Visual Effects** tab. Once there, I selected the **Custom** Preferences for Window Decoration (you can use the Filter function in the upper left corner of the **CompizConfig Settings Manager** window) by clicking on the **Window Decoration** icon and added the word "emerald" in the **Command** dialog box.

[COLOR="Blue"]**BINGO!**[/COLOR] It worked.

Thank you **dpar** for pointing the way.

Oh, and because I run with nVidia, I also issued the following command in the TERMINAL:

> sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Okay, so that's three things - but you might not need to do this last step unless you are using nVidia.

And one last thing - reload XWindows. Okay, okay! So that's four things.

Thank you! Thank you! Thank you! Thank you! Thank you!

---

### Post by phalkon30 on 2007-10-19
Ahh, so I'm not the only one with this problem. I've got an FX5900, I had desktop effects disabled before upgrading to Gutsy, but if I try to enable them, I lose the title bars. You also lose the ability to move windows around.

Is this possibly an nVidia thing?

---

### Post by mtgrocks04 on 2007-10-19
If you have emerald installed then go to menu-settings-advanced desktop settings which will open compiz settings manager (you can also use alt-f2 and run ccsm). From there activate the plugin window decoration and enter emerald in the "command" line in the options for that plugin. This fixed the issue for me.


As for the ability to move the windows and such, you need to activate those plugins as well in the compiz settings manager.

---

### Post by soctu on 2007-10-19
Unfortunately putting emerald in the command line did not work for me. I have no borders, I can't move firefox from the top of the screen (it covers my applications which I have placed on the top toolbar) none of the alt-F4 whatever will not work so i have to close firefox to get to the terminal and I can't cut and paste code into the terminal window.When I click on the bookmarks the bookmarks appear behind firefox so I can't access anything I bookmarked.
All this because I upgraded from fiesty to gutsy. Fiesty I had everything working fine the cube effects, even the atlantis fish. This has been the worst upgrade I've experienced even worse than upgrading to fiesty where I faulted to the command line and had to use my 
dapper cd and upgrade to edgy and then to fiesty. I have a Nvidia 7300 card with 256mb of memory on it. Sorry for the rant but I need get this stuff fixed before my family kills me ;-)

edit:
I GOT MY BORDERS BACK system->preference->appearance->visual effects I set it to Extra now the extra did not work (ie i don't have my cube and effects :-( BUT I did get my borders back and my 
Bookmarks menu works correctly now. UNTIL I REBOOT THE COMPUTER! Then I have to do the whole system->preference->appearance->visual effects thing again :-(

---

### Post by Grivooga on 2007-10-20
Installing the settings manager and turning off the desktop wall restores my windows borders reliably (atleast so far).
edit: nvm they're broken again.

---

### Post by Tux Aubrey on 2007-10-20
For gnome desktop users (the ordinary version of ubuntu), open a terminal and try:

> 
metacity --replace

This should turn off emerald and compiz and return you to your "vanilla" desktop.  This is not a solution to the original problem but will give you a usable desktop.

Personally, I think the lack of an obvious option to turn off compiz once enabled is a bit rude.  It really gets on my nerves when its on by default.

---

### Post by Grivooga on 2007-10-20
Well the visual effects were nice for the minute or so they worked. Then my window borders disappeared and though they'll pop back up if I go about disabling and enabling plug-ins they never seem to stay for long. Longest was a few minutes when I made post above thinking I had this licked. Atleast I don't have a problem turing it off. The appearance panel has always been available though the tabs on top might be obscured.

---

### Post by Mondoman on 2007-10-20
I am also having the "missing window borders and title bar" issue.  I upgraded to Gutsy from Feisty and things seem to work fine (but no fancy effects of course) if I leave the Visual Effects off.  When I select Normal or Extra, the (display manager?) restarts and repaints the screen but the windows are missing borders and title bars (thus no moving/closing/resizing them).
I have the restricted source nVidia video driver installed.
Any suggestions on how to make the fancy Compiz features work?

---

### Post by dpar on 2007-10-20
This link may help you guys.

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by GSF1200S on 2007-10-20
> **Mondoman said:**
> I am also having the "missing window borders and title bar" issue.  I upgraded to Gutsy from Feisty and things seem to work fine (but no fancy effects of course) if I leave the Visual Effects off.  When I select Normal or Extra, the (display manager?) restarts and repaints the screen but the windows are missing borders and title bars (thus no moving/closing/resizing them).
I have the restricted source nVidia video driver installed.
Any suggestions on how to make the fancy Compiz features work?

Im still trying to figure out why, but im having similar issues- I use KDE, and KDE often informs me that kwin (kde's version of metacity) has crashed often when compiz is enabled. This sounds like whats happening to some of you- I thought it was a kwin problem, but this appears to be a compiz problem. 

Please post the contents of /etc/X11/xorg.conf

Do you have no borders as soon as you enable the effects, or do the borders dissapear after a little while.

You can try:

```
compiz --replace
```

but I dont know if it will help you...

---

### Post by Mondoman on 2007-10-21
OK, as soon as I tried the "compiz -- replace", the display "reset" and all the window title bars and frames vanished, just as when I tried the "normal" or "extra" choices in the appearance manager.   What am I doing wrong?
 Here's the listing from the terminal window:
```

armand1@BluBox:~$ sudo compiz --replace
[sudo] password for armand1:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

And here is my /etc/X11/xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Nvidia GeForce 6200 AGP"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Samsung SyncMaster205BW"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia GeForce 6200 AGP"
	Monitor		"Samsung SyncMaster205BW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by DutyDuty on 2007-10-21
Try either

```
compiz --replace
```
or 
```
emerald --replace
```

---

### Post by Mondoman on 2007-10-21
DD - as shown in my post below, "compiz --replace" causes the problem, it doesn't solve it.
Here's what happens with "emerald --replace":
```
armand1@BluBox:~$ emerald --replace
The program 'emerald' is currently not installed.  You can install it by typing:
sudo apt-get install emerald
bash: emerald: command not found

```

---

### Post by DutyDuty on 2007-10-21
Might I suggest installing emerald?
```
 sudo apt-get install emerald
```

---

### Post by Jaxilian on 2007-10-21
I would call this Compiz fusion a BIG failure. It doesn't work at all. :mad:

---

### Post by Mondoman on 2007-10-21
DD -
OK, I installed emerald using synaptic, then rebooted my system.  Still no good.  Here's what happens:
If I do "emerald --replace", the terminal window just sits there and doesn't give me a prompt again.
If I do "compiz --replace", I get the same missing title bars and window frames, with a slightly different list of status messages:
```
armand1@BluBox:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32


```

---

### Post by Mondoman on 2007-10-21
I notice that the status messages indicate "xgl" is not present.  Is this something I need to install in my system for compiz to work properly?  If so, what exact package do I need? Thanks for your efforts.

---

### Post by Mondoman on 2007-10-21
OK, it looks like I was on the right track in my previous post.  I uninstalled emerald, then installed xserver-xgl and rebooted.  Now, changing to normal or extra in Visual Effects/Appearance actually works!
Moral of this story: pay attention to the diagnostic messages generated by "compiz --replace" rather than getting sidetracked with alternate managers such as emerald.

---

### Post by davidsrsb on 2007-10-22
I tried installing xserver-xgl on my Dell with a Nvidia 7300LE and after the nvidia splash screen went to a black screen with just a cursor. I had to go to rescue mode and remove the package with aptitude to recover.

---

### Post by MrKirby on 2007-10-23
> **Mondoman said:**
> OK, it looks like I was on the right track in my previous post.  I uninstalled emerald, then installed xserver-xgl and rebooted.  Now, changing to normal or extra in Visual Effects/Appearance actually works!
Moral of this story: pay attention to the diagnostic messages generated by "compiz --replace" rather than getting sidetracked with alternate managers such as emerald.

My borders were lost, strangely, right after I went to system>administration>network   and then the network window did not fill and just hung there...?  Either way, I'm glad I found this thread, as I did exactly what you said and installed xserver-xgl and restarted.  Now everything works fine again.  I did not have emerald or anything installed, so I didn't have to worry about that.  What do you think caused this?  Everything was working fine until that program crashed or something.

Using Nvidia, and if it's related, ndiswrapper for my broadcom wireless network card.

---

### Post by MrKirby on 2007-10-23
> **davidsrsb said:**
> I tried installing xserver-xgl on my Dell with a Nvidia 7300LE and after the nvidia splash screen went to a black screen with just a cursor. I had to go to rescue mode and remove the package with aptitude to recover.

I noticed you're using feisty fawn (or maybe you didn't update your profile?).  When I was using beryl and emerald in feisty, my problem was that emerald was not running yet. I had to add an entry into my sessions list to make sure it ran on boot. After emerald was running, I had title bars. I don't exactly remember what I did there, but I'm sure you can google it. Be careful, as this thread is for Gutsy, 7.1 users.

---

### Post by MrKirby on 2007-10-23
> **dpar said:**
> This link may help you guys.

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

BTW this link was very helpful. After i got my title bars and borders back, after switching from feisty i didn't know how to tweak everything out. Thanks!

---

### Post by Goupit on 2007-10-23
I'm also a nvidia user. Had the same problem. I followed the instructions mentioned in the blog that dpar posted.

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

 I first used the command that is said.

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

 Then I used the synaptic package manager and installed the nvidia-xconfig. The system also removed the nvidia-glx and everything is now working great.

---

### Post by il-luzhin on 2007-10-23
I can't even get rolling on a fix.  This is the same after twice re-installing ccsm.

```

luzhin@luzhin-desktop:~$ ccsm
/home/luzhin/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
    self.Context.Plugins.items ())
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
    self.PluginList = filter (lambda p: FilterPlugin (p[1]),
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
    return not p.Initialized and p.Enabled
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
luzhin@luzhin-desktop:~$ 

```

---

### Post by davidsrsb on 2007-10-23
I had forgotten to update my profile, I am running Ubuntu 7.10

---

### Post by ABX on 2007-10-24
> **asmiller-ke6seh said:**
> Same, here. When I enable either the **Normal** or **Extra** Visual Effects, I lose the Title Bar on any and all windows (existing or new), and I also lose the ability to drag and drop my applications windows around the screen.

If I turn off Visual Effects, I get my title bars back and my ability to drag and drop applications windows.

When the Title Bars dissapear, so do the windows controls icons (minimize, mazimize, exit).

I use nVidia on my System 76 laptop. I installed the latest System 76 drivers and rebooted my system both before (and after) installing Gusty Gibbon.

--------LATER-----------------------------------------------------------------
I found the answer later in this thread; see message #12.

I did two things to solve this problem, thanks to **dpar** pointing to a blog by Forlong hosted by some great guys in Germany. This is what I love about being an Ubuntista -- It's the Community!!!


FIRST: using the Synaptic Package Manager, I downloaded EMERALD by searching for "emerald" and installing it, then

SECOND: I went to **System -> Preferences -> Appearance** and I selected the **Visual Effects** tab. Once there, I selected the **Custom** Preferences for Window Decoration (you can use the Filter function in the upper left corner of the **CompizConfig Settings Manager** window) by clicking on the **Window Decoration** icon and added the word "emerald" in the **Command** dialog box.

[COLOR="Blue"]**BINGO!**[/COLOR] It worked.

Thank you **dpar** for pointing the way.

Oh, and because I run with nVidia, I also issued the following command in the TERMINAL:



Okay, so that's three things - but you might not need to do this last step unless you are using nVidia.

And one last thing - reload XWindows. Okay, okay! So that's four things.

Thank you! Thank you! Thank you! Thank you! Thank you!

Thanks, this solved my issue with borders and unusable terminal under normal / extra visual settings.

---

### Post by konungursvia on 2007-10-25
I still have the same sort of problem since upgrading to Gutsy. I run Beryl and Emerald, on nvidia GeForce 4 440 and had it all fine in Feisty. Maybe someone is right that emerald is not really running. When I type gtk-window-decorator --replace, I get

Window manager warning: Failed to load theme "": Failed to find a valid file for theme 

and when I try to make sure emerald is running by typing emerald in the shell, i get

emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

My xorg.conf looks like this:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
	Load		"dbe"
	Load		"dri"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
	Option          "XkbOptions"    "compose:ralt"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option 		"XAANoOffscreenPixmaps"
#	Option          "UseDisplayDevice"    "DFP"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 440 Go]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Any ideas? Thanks

---

### Post by CoolDreamZ on 2007-10-26
I have a similar problem on a dual-head machine. The first (LHS) display has title bars the second (RHS) display does not. I have tried the suggestions on this thread and followed the advice on this link [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") with mixed results. The second display stubbornly refuses to display Window decorations under any circumstances.

Using the "emerald" decorations worked on the LHS display the first time I tried it (although I got a popup message containing a GNOME error message - unable to load settings manager) - but still no title bars on the second display.

Since then I haven't been able to get emerald to work again, despite several restarts of the X-server and Linux. The compiz settings manager appears to have different settings for Screen 0 and Screen 1, however they do not seem to work independently - changing a setting on one Screen affects the setting on the other.

The nvidia setting > sudo nvidia-xconfig --add-argb-glx-visuals -d 24 did not make any difference.

---

### Post by Jpfan017 on 2007-10-26
It's enabling water effects for me. When I do it won't let windows decorator stay active, it keeps reseting it as well as some of the other plugins. I have to uninstall compiz and emerald and reinstall entirely to get everything to work again. I can then edit everything else with no problem. The minute I reenable water effects the borders disappear and the plugins reset and everything breaks again. I've tried it like 4 times. It always breaks after I enable water plugins.

If I leave it off and set the command for windows decorator to emerald, the borders, and all the other plugins work just fine. I'm almost positive it's when you enable the water effects that things start breaking.

---

### Post by CoolDreamZ on 2007-10-29
Have changed to a spanned (TwinView) nvidia setup (rather than two independent X displays) and it works fine most of the time. Sometimes the title bars disappear, I can get them to re-appear by mousing over the minimize/maximize/close buttons. I think this is a compiz bug?

---

### Post by pclos on 2007-11-09
I've experienced this a few times and I believe that it is a bug in the Compiz and Beryl merger.  If you update your system while using Compiz or Beryl, you have to change your settings to use Compiz fusion instead of Compiz or Beryl.  Hope this helps...

---

### Post by warmwaddle on 2007-11-09
I got it to work by adding the gtk window decorator and compiz to the startup program list and rebooting. 

System > preferences > sessions for the startup program list.

---

### Post by Mo9a7i on 2007-11-17
Thank you very much  [B][COLOR=Red]asmiller-ke6seh 
[/COLOR][/B]your solution solved my problem ,, i'm runing **ubunto 7.1** and compizfusion on ,,

enabling the desktop effects and adding that in the command line fixed it very smoothly ,,

i was disparate  and here i'M :)

---

### Post by staib on 2007-11-18
I've tried to run desktop effects in 7.10 on an Nvidia card but like others am immediately losing the window 'frames' - I have followed the clear advice in Furlong's blog. And for a while get to see the frames once effects are enabled BUT you can't drag the windows around and within a few minutes just lose the frames again...
If I run the Emerald Theme Manager and try to get some themes (the GPL ones) nothing happens - at least nothing on screen - should it?  Do I need this to get compiz-fusion running?

---

### Post by Netgull on 2008-01-03
Just to have one more clue in case somebody needs it...
I am using 7.10 and have an nVidia GeForce 7400.
I had also the missing title bar problems.

Here is how I solved it:
1) Installed nVidia driver through Envy (the one from the Restricted Driver Manager doesnt produce a working xorg.conf for some reason)
2)System restart (not Xserver).
3)Try to enable Extra Visual Effects. The system says the restricted driver needs to be enabled (I know it IS installed and enabled but it says so...).
Click yes.

If you click ok and restart and then try to have Extra Effects it WONT WORK (titles will be missing). So go to step 4.

4)Now you can enable the Extra effects. After enabling restart Xserver by Ctrl Alt Backspace and all the effects are working!!
Now you can also restart the system.

I have absolutely no idea why this worked but it solver the problem for me twice. Someone with more experience may be able to see something through this.

---

### Post by letired on 2008-01-19
soup.
I have a slight remix of this problem: instead of not showing window borders, x restarts when visual effects are switched to normal/extra. On restart, no settings have been changed. In failsafe mode I am allowed to switch, only to get an error message saying something saying it couldn't switch to another desktop mode - basically, no help there.
Prior to adding AddARGBvisuals to xorg.conf, I too was just getting the missing borders.

I'm on an Nvidia Geforce 8600M GT card. Installing xserver-xgl resulted in x restarting right after login, instead of after changing desktop modes.

Here's my xorg.conf (yay for spoiler tags):

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:09:35 PST 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:10:32 PST 2007
# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CMO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600M GT]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8600M GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900_60 +0+0"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection


---

### Post by CoolDreamZ on 2008-02-04
This has been confirmed as a bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508")

---

