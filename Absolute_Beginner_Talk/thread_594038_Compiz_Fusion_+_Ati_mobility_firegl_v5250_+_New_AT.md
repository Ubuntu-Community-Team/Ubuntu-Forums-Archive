---
title: "Compiz Fusion + Ati mobility firegl v5250 + New ATI 8.42.3 drivers"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Andross707 on 2007-10-27
OK,
so I've been trying to get these new drivers installed as they are said to give my graphics card the ability to use its 3D capabilities so that I can finally use Compiz Fusion and all that jazz. I tried to install it and I think it managed to install (I went to  [http://wiki.cchtml.com/index.php/8.42.3]("http://wiki.cchtml.com/index.php/8.42.3") and ran the .run file from the terminal and after a official looking ATI install screens it said the install was complete). I restarted and tried to change the System settings -> monitor and display -> hardware setting to either fglrx and the ATI driver listed and both broke my X forcing me to reconfigure X on restart. I've carefully tried to follow [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) , but nothing is seeming to work. The ATI catalyst control center button in my KDE menu that used to give me an error ( I forgot what it was) now just doesn't do anything.

Is there any hope to escape from VGA?

---

### Post by fredb987 on 2008-01-31
Wow... 3 months and not a single reply!

Did you ever get the ATI drivers working? I'm currently using the fglrx driver and have everything working (Compiz, etc.) except DRI. I'm happy with my setup, but can't help wondering if I'm missing out on tapping in to all the capabilities of my GPU with the ATI 8.42 driver. :confused:

Here's my hardware:
ThinkPad T60p
ATI Mobility FireGL V5250 w/ 256MB

---

### Post by softtower on 2008-02-04
There have been several similar topics on this board recently, all about ThinkPads with this retarded ATI hardware. No, the latest driver is buggy and does not work well. The best proprietary driver to use is still what's included into Ubuntu 7.04 by default. This is what I rolled back to using. It's really fast, hibernates/suspends, does not produce any errors in XOrg log file and movies (of various formats) do not consume any CPU. The only thing it's missing is 3D support for Compiz.

---

### Post by maphilli14 on 2008-03-11
Just did the Hardy update (previously Gutsy and previously Feisty) on my Lenovo Thinkpad T60p.

```
 lspci | grep 5250
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250]

```

At this point I'm totally pissed at both Lenovo and my workplace for picking this stupid POS hardware config.

What options do I have?  Windows?

Under Hardy I seem to be stuck in Mesa mode on the fglrx drivers.

```
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3)

```

EVEN after issuing the commands listed here [http://ubuntuforums.org/showthread.php?t=673590]("http://ubuntuforums.org/showthread.php?t=673590")

I seem to have good performance under this config but no control over resolution and suspend/hibernate.

I'm committed to Ubuntu and really like it, I just need to overcome this lousy hardware and don't seem to be alone.

I'm a 1st time poster but am a quick study and willing to accept any help or troubleshooting.  Just guide me!  :)

Mike

PS I'm in a dual boot and my XP changes desktop resolution ALL THE TIME!!! I really do hate this video card!  Save me LINUX!!!!

---

### Post by Andross707 on 2008-03-12
I'm still in the same boat and I've yet to find a solution on this forum that will allow me to see the magic spinning workspace cube with my video card. Does anyone have a solution to enable the 3D properties of this video card or am I just screwed?

---

### Post by Andross707 on 2008-03-12
Fred, how did you get your system working/ what all did you get working on your T60p?

---

### Post by maphilli14 on 2008-03-13
I posted a vote over in the Laptop forum in the off chance someone who can help frequents that list and not the beginner one.

[http://ubuntuforums.org/showthread.php?t=722502]("http://ubuntuforums.org/showthread.php?t=722502")

Mike

---

### Post by rockinlinux on 2008-03-13
i have a ati card in ym desktop. i used envvy and it works great

---

### Post by maphilli14 on 2008-03-13
Envy worked well for me to install the fglrx drivers in feisty and gutsy, but its not suppored on hardy.  I grabbed EnvyNG and it bombs on the fglrx drivers and didn't work well on the 8.3 ATI drivers.

I'm stuck in vesa 800x600 mode on my T60p still.

Someone HELP!

](*,)

---

### Post by maphilli14 on 2008-03-14
Update:

I seem to be having more success with the ati-driver-installer-8.42.3-x86.x86_64 after some Hardy updates to Xwin.  I've got it now with desktop effects with these steps:

1) Run the ati-driver-installer-8.42.3-x86.x86_64
2) Reboot
3) Enable driver in System / Admin / Hardware Drivers (it's off by default even after install
4) add these lines to xorg.conf

     	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x800" "1024x768" "800x600" "640
x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x800" "1024x768" "800x600" "640
x480"
	EndSubSection


5) Enable desktop effect
6) option, add advanced compiz wizard for cube effects etc...


YEA!!!   :guitar:

Mike

---

### Post by Andross707 on 2008-03-15
I tried your instructions mike, but now when I get the part where I try to enable desktop effects it gives me the hourglass for a few seconds then says "could not enable desktop effects" and drops me back

---

### Post by maphilli14 on 2008-03-15
I'm attaching a copy of my xorg.conf (happily renamed HARDY-BEST.txt).

I'm not sure the exact steps I took to get here other than this... are you running Hardy?

Mike

---

### Post by maphilli14 on 2008-03-23
More updates:

I have issues (BAD ONE's, but that's another story), with X reloading (a-la ctrl+alt+bckspace)
while I type rapidly with mixed case, hitting the left shift on and off.

As such, I loaded up the latest ATI drivers:

ati-driver-installer-8.443.1-x86.x86_64

This rendered me in pretty bad shape with no desktop effect, poor resolution etc...


Then I gave up fighting and hit EnvyNG again.  Viola!

I'm back in business with all the coolest compiz stuff, but am still stuck with the reloading issues!

HELP!!!!

Mike

---

### Post by misterhead on 2008-03-24
> **Andross707 said:**
> I'm still in the same boat and I've yet to find a solution on this forum that will allow me to see the magic spinning workspace cube with my video card. Does anyone have a solution to enable the 3D properties of this video card or am I just screwed?

Dell Latitude D810, ATI Radeon Mobility X600.
I originally got it to work with the appropriate proprietary driver AND after installing the dreaded Xserver-xgl package. It works great, but I found a few drawbacks to running xserver-xgl including a "shadow outline" glitch, slow X loading, and problems "dual monitoring".

I have since re-installed from the ground up (without Xserver-xgl) when I stubled accross this...

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

It works GREAT!... at least for me, that is. It's the new driver, but other crap needs to be removed, and new stuff needs to be done, but everything is here that needed to be done to mine.

Hope this helps somebody.

---

### Post by hsjC on 2008-03-24
This is what I follow every time:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

I got a dual core opteron + ati x1900 aiw. Everything runs fine with the above setup... compiz and dri.

For the proprietary driver to work, you can't have xgl. But the driver comes with AIGLX, which does the fancy desktop cube stuff anyway.

---

### Post by maphilli14 on 2008-03-30
hsjC,

   Are you using a Lenovo?  If so which model?  Also what about suspend resume?

TIA,

Mike

---

### Post by hsjC on 2008-04-13
Sorry maphilli14, I have an ati for my desktop. Suspend works ok but I lose sound when resuming from suspend. Haven't tried hibernate.

I also have a lenono z61t laptop with gusty on it. Everything works fine: compiz, suspend...

---

### Post by zouriel on 2008-07-07
Hey guys... im using a T60p compiz fusion and the latest ATI driver ([https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-6-x86.x86_64.run))

for the install of the driver i used for hardy

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The only issue I am having is that hibernation takes a little longer than i would like for it to kick over.


Here is my /etc/X11/xorg.conf

Some of this was a carry over from Fiesty and or Gutsy that i commented out.

```

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
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	
	Option "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc101"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"

EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
	Option	    "SHMConfig" "true"
	Option	"SHMConfig" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
#	HorizSync    30.0 - 85.0
#	VertRefresh  50.0 - 80.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
Option "XAANoOffscreenPixmaps" "True" #->This one IS absolutely NEEDED! It shouldn't be missed!
Option "VideoOverlay" "on" #-> In order to get hardware XV video playback!
Option "TexturedVideo" "True" #->New!! Plays accelerated video! Important!
Option "TexturedVideoSync" "True" #-> Synchronizes Textured Video
##Option "Textured2D" "True" #->Experimental! See Note 1...
Option "TexturedXrender" "True" #->Experimental! See Note 2...
Option "UseFastTLS" "2"  # ->Sincerely I don't know what this one does but it is suggested by a lot of people...
Option "BackingStore" "True"  # ->Helps alot. See Note 3...
##Option "MaxGARTSize" "000" #->For PCI-Express cards it sets the amount of VRAM to be allocated by the driver. "000"=Put your amount of VRAM here. See Note 4...

Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
#		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group        "video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "XVideo" "Enable"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "1"
EndSection
```


Thinkfinger .30 works well with the fingerprint reader 
for LAN and WLAN im using WICD with little to no issues.... more of little annoyances

---

### Post by Andross707 on 2008-07-10
> **zouriel said:**
> Hey guys... im using a T60p compiz fusion and the latest ATI driver ([https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-6-x86.x86_64.run))

for the install of the driver i used for hardy

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The only issue I am having is that hibernation takes a little longer than i would like for it to kick over.


Here is my /etc/X11/xorg.conf

Some of this was a carry over from Fiesty and or Gutsy that i commented out.

```

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
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	
	Option "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc101"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"

EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
	Option	    "SHMConfig" "true"
	Option	"SHMConfig" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
#	HorizSync    30.0 - 85.0
#	VertRefresh  50.0 - 80.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
Option "XAANoOffscreenPixmaps" "True" #->This one IS absolutely NEEDED! It shouldn't be missed!
Option "VideoOverlay" "on" #-> In order to get hardware XV video playback!
Option "TexturedVideo" "True" #->New!! Plays accelerated video! Important!
Option "TexturedVideoSync" "True" #-> Synchronizes Textured Video
##Option "Textured2D" "True" #->Experimental! See Note 1...
Option "TexturedXrender" "True" #->Experimental! See Note 2...
Option "UseFastTLS" "2"  # ->Sincerely I don't know what this one does but it is suggested by a lot of people...
Option "BackingStore" "True"  # ->Helps alot. See Note 3...
##Option "MaxGARTSize" "000" #->For PCI-Express cards it sets the amount of VRAM to be allocated by the driver. "000"=Put your amount of VRAM here. See Note 4...

Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
#		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group        "video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "XVideo" "Enable"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "1"
EndSection
```


Thinkfinger .30 works well with the fingerprint reader 
for LAN and WLAN im using WICD with little to no issues.... more of little annoyances


The installation and a quick cut and paste of the Xorg.conf file here into mine fixed my problems! I can now use visual effects (System > Prefrences > Appearances > Visual Effects). Thank you.

One small thing though, when no windows are up and I'm just at the desktop itself there are these black lines over my mouse pointer... so far it seems purely aesthetic but I'm wondering if you have it too...

---

