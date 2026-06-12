---
title: "New VideoCard: tvtime : No Input signal. Why?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-15
Hi, 

I plugged my antenna in the tv card.
First isntalltion of tvtime, and config :=> OK
  
I start the prog in root to be sure of no prob wiht permissions.
and blue screen : No Input Signal 
  
This card was working under windows.
  
Someone could help me ?? (maybe my list of tv channel stations has to be set up?)
  
Thank you very much, 

Pat

---

### Post by BoyOfDestiny on 2005-11-15
[QUOTE=patrick295767]Hi, 

I plugged my antenna in the tv card.
First isntalltion of tvtime, and config :=> OK
  
I start the prog in root to be sure of no prob wiht permissions.
and blue screen : No Input Signal 
  
This card was working under windows.
  
Someone could help me ?? (maybe my list of tv channel stations has to be set up?)
  
Thank you very much, 

Pat[/QUOTE]

It would help to know what the card model is. There is no need to run tvtime as root.

You can try pressing "i" in tvtime and see if it changes to the proper input. 

Also, you can check multimedia selector in the system preferences and change the default video input source.

Good luck

P.S My leadtek winfastxp works great with tvtime. If you have that you are in luck.

---

### Post by patrick295767 on 2005-11-16
[QUOTE=BoyOfDestiny]It would help to know what the card model is. There is no need to run tvtime as root.

You can try pressing "i" in tvtime and see if it changes to the proper input. 

Also, you can check multimedia selector in the system preferences and change the default video input source.

Good luck

P.S My leadtek winfastxp works great with tvtime. If you have that you are in luck.[/QUOTE]

Hi, 
  
First, thank you very much for your reply and your support !
  
I have a rage ati AGP 128 all in wonder (from my dad) ... I'll ask him the model. 
  
Concerning pressing 'i', I tried several times but no changes. => blue screen and "No Input".
  
I tried to click in video input in the menu
but it doesnt enter in another submenu.
  
I can press enter on 'input menu' but no effect. 
(yellow menu that is in the middle of screen of tvtime)
   
I dont really know what to do.
  
Maybe the channels not set up. I dont really know how to solve this problem.
  
Maybe another program like tvtime ? 
  

thank you very much , 

 patrick

---

### Post by oskude on 2005-11-16
[QUOTE=patrick295767]I have a rage ati AGP 128 all in wonder
Maybe another program like tvtime ?[/QUOTE]
```
apt-cache show gatos
```
if you can see video from fbas/s-video input but cannot find any channels on tv-input, you propably have the wrong tuner configured...

---

### Post by patrick295767 on 2005-11-16
[QUOTE=oskude]```
apt-cache show gatos
```
if you can see video from fbas/s-video input but cannot find any channels on tv-input, you propably have the wrong tuner configured...[/QUOTE]
i typed:
```
apt-cache show gatos
```
 
and got :
> Package: gatos
Priority: extra
Section: universe/misc
Installed-Size: 556
Maintainer: Christian Bayle <bayle@aist.enst.fr>
Architecture: i386
Version: 0.0.5-14ubuntu1
Depends: libc6 (>= 2.3.2.ds1-4), libgatos0 (>= 0.0.5), libgcc1 (>= 1:3.4.1-3), libibtk0, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), netpbm, libjpeg-progs
Suggests: mpeg2dec
Filename: pool/universe/g/gatos/gatos_0.0.5-14ubuntu1_i386.deb
Size: 137812
MD5sum: dffdqfdqsfdsq
Description: ATI All-in-Wonder TV capture software
 The General ATI TV and Overlay Software (GATOS) suite for
 capturing video.  This package does not require kernel
 patches, and includes:
   * xatitv: GUI TV-in-a-window application
        GUI access to all GATOS functionality, save tv-out.
   * atitv: Simple text-mode program
        Basic functionality to record video and toggle tv-out.
   * atitoppm:
   * atitogif:
   * atitojpg:
        YUV conversion utilities
   * yuvsum: video field to frame converter
        Averages all images in gatos.yuv (must all
        be same size).
   * atisplit: YUV conversion to ucbmpeg
        This splits the output file for MPEG encoding.
  This software is not intended to support most recent ATI AIW Radeon
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu



---

### Post by patrick295767 on 2005-11-16
tvtime is telling me :
no /dev/video0
  
I looked in the folder /dev/
and yes ... /dev/video0 not found ...
I dont really know what to do...

thank you, 
pat'

---

### Post by patrick295767 on 2005-11-16
I tried : 
   
> insmod bttv
insmod: can't read 'bttv': No such file or directory
  
also:
> insmod tv-driver
  
nothing changed ..

---

### Post by patrick295767 on 2005-11-16
I also tried :
> modprobe bttv
  
that's giving nothing 

#
#

---

### Post by oskude on 2005-11-16
"apt-cache show gatos" shows information about the program "gatos"... looking at your card "ati all-in-wonder"... you asked "Maybe another program like tvtime ?"... got it ? :)

for "/dev/video0" dont know nothing, sry. 
but i could think that the drivers (when they work) would do this "/dev/video0" device (thats just my NOT-knowing guess)..

---

### Post by patrick295767 on 2005-11-16
Thank you again & again !!!
 i installed gatos (apt-get install gatos)
  
  I typed the code:
```
apt-cache show gatos and got the following :
```
  
> Package: gatos
Priority: extra
Section: universe/misc
Installed-Size: 556
Maintainer: Christian Bayle <bayle@aist.enst.fr>
Architecture: i386
Version: 0.0.5-14ubuntu1
Depends: libc6 (>= 2.3.2.ds1-4), libgatos0 (>= 0.0.5), libgcc1 (>= 1:3.4.1-3), libibtk0, libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), netpbm, libjpeg-progs
Suggests: mpeg2dec
Filename: pool/universe/g/gatos/gatos_0.0.5-14ubuntu1_i386.deb
Size: 137812
MD5sum: 5d3705afba99959669c30a47d1017886
Description: ATI All-in-Wonder TV capture software
 The General ATI TV and Overlay Software (GATOS) suite for
 capturing video.  This package does not require kernel
 patches, and includes:
   * xatitv: GUI TV-in-a-window application
        GUI access to all GATOS functionality, save tv-out.
   * atitv: Simple text-mode program
        Basic functionality to record video and toggle tv-out.
   * atitoppm:
   * atitogif:
   * atitojpg:
        YUV conversion utilities
   * yuvsum: video field to frame converter
        Averages all images in gatos.yuv (must all
        be same size).
   * atisplit: YUV conversion to ucbmpeg
        This splits the output file for MPEG encoding.
  This software is not intended to support most recent ATI AIW Radeon
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu



---

### Post by patrick295767 on 2005-11-19
I have a /dev/video1394
  
no /dev/radio
(i tried to install gqradio) (not working)
  
i also tried : ln -s /dev/video1394 /dev/video0
not working either :-(

---

### Post by patrick295767 on 2005-11-21
Is there someone who knows maybe ??

---

### Post by oskude on 2005-11-21
well,

my quick google searches dont say any good about ati-all-in-wonder tv tuner and linux. so you better get another card or mail ati and ask why theres no linux driver ;)

---

### Post by Mustard on 2005-11-21
[QUOTE=patrick295767]Is there someone who knows maybe ??[/QUOTE]

Are you still running Hoary Hedgehog?

I had trouble with a completely different brand of TV card on Hoary, due to an 'dga not supported' error.  Upon upgrading to Breezy my TV card was functional using xawtv.  It's long shot, but you never know.

---

### Post by Paul Chang on 2005-12-10
I got a webcam and ATI AIW 7500, and installed GATOS. When I type "tvtime-scanner", it is checking the webcam. In /dev/, only /dev/video0 shows. How can I redirect "tvtime" to the ATI AIW? Thanks a lot for any help!

---

### Post by walopower on 2006-01-05
Same problem, have aiw 9800le and already installed fglrx and gatos with no errors.
But in /dev/video0 (no videoX either) not exist and any capture program (xawtv, xatitv and several else) doesn´t work.
Remote control is working directly.

---

### Post by patrick295767 on 2006-01-05
[QUOTE=Mustard]Are you still running Hoary Hedgehog?

I had trouble with a completely different brand of TV card on Hoary, due to an 'dga not supported' error.  Upon upgrading to Breezy my TV card was functional using xawtv.  It's long shot, but you never know.[/QUOTE]
 
Hi !! 
Thank you very much first for your reply, 
  
I tried with the breezy, and results were similar ... 
I'll install again breezy to try again I guess ... 

thank you !!

---

### Post by patrick295767 on 2006-01-05
[QUOTE=Paul Chang]I got a webcam and ATI AIW 7500, and installed GATOS. When I type "tvtime-scanner", it is checking the webcam. In /dev/, only /dev/video0 shows. How can I redirect "tvtime" to the ATI AIW? Thanks a lot for any help![/QUOTE]
  
This can eventually gives you some ideas with the /dev/video0
[http://doc.ubuntu-fr.org/materiel/webcam_logitech_msn](http://doc.ubuntu-fr.org/materiel/webcam_logitech_msn)
  
I dont know more for the moment ...

---

### Post by patrick295767 on 2006-01-05
[QUOTE=walopower]Same problem, have aiw 9800le and already installed fglrx and gatos with no errors.
But in /dev/video0 (no videoX either) not exist and any capture program (xawtv, xatitv and several else) doesn´t work.
Remote control is working directly.[/QUOTE]
  
Linux and drivers, is kind of horrible, since slackware 3.1, ... so long time ago, isnt it ?
  
I have soo much problems with drivers me, 
logitech webcam quick messenger, ati all in wonder capture and tuner, and usb logitech microphone (with skype)
not working ... it's terrible drivers ....
Also also 
I bought the last microsoft mouse wireless optical with the vertical and horizontal scrolling ... Imagine ... 
Of course, not working... 
  
So, about 4 devices that are rather easy stuffs are not working. 
I thought that with Linux Ubuntu, everthg would be different and I could discover a total freedom and stable system... 
  
I still have some hopes to make it...
  
Good Luck and Greetings, 

Patrick

---

### Post by aev on 2006-01-05
Hi,

i create 

MAKEDEV video 

and then I have 

/dev/video0.

 But after restart it disapears :confused: So when I try zpping TV or just try 

cat /dev/video0 ... this says no such device. Does anyone know how to set up the video4linux devices /dev/video0?

thanks.

---

### Post by poofyhairguy on 2006-01-05
Gatos is only way. Try to apt-get it.

I have an All-In-Wonder, but I think I will trade it for a real TV card.

---

### Post by patrick295767 on 2006-01-06
[QUOTE=poofyhairguy]Gatos is only way. Try to apt-get it.

I have an All-In-Wonder, but I think I will trade it for a real TV card.[/QUOTE]
  
Good to see that I am not alone in same shit with linux drivers for this all in wonder ... In windows, it 's really an amazing tv card !
  
Courage !
  
Greetz

Pat'

---

### Post by walopower on 2006-01-06
There is also discussion of same subject.
[http://ubuntuforums.org/showthread.php?t=46496](http://ubuntuforums.org/showthread.php?t=46496)

---

### Post by patrick295767 on 2006-01-06
[QUOTE=walopower]There is also discussion from same subject.
[http://ubuntuforums.org/showthread.php?t=46496](http://ubuntuforums.org/showthread.php?t=46496)[/QUOTE]
  
Thank you !
Ahh Drivers, what a problem & fight  ! :-)

---

### Post by Garibaldi3489 on 2007-01-25
I've been reading your posts/guide about the ATI All-In-Wonder capture card on Linux. I have an ATI AIW 9600 (not sure about the TX) and would like to get it working on my Kubuntu 6.10 install. I installed Gatos and the ati driver from their site, although fireglcontrolpanel doesn't work for some reason even after the install. Anyway reading through your guide a lot of it made sense but I'm not sure about this part:
Your graphic card driver must be Radeon ATI (Xorg modular 7.0 or 7.1) and not ATI fglrx!!

What does that mean? I am not sure what mine is or how to change it to Radeon ATI (Xorg modular 7.0 or 7.1). Here's my Xorg.conf if that helps:
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "ServerLayout"

#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "610"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "610"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


---

