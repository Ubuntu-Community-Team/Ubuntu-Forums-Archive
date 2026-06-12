---
title: "Xserver and ATI drivers"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Flavian on 2006-06-05
Hi fellows.
I finally installed Ubuntu 6.06 on my laptop ( I had some troubles in the past with 5.04 [5.10 never worked] but finally was able to get the Xserver to work propperly)
Now though it seams to be different.
In the past I just opened /etc/X11/xorg.conf and put "vesa" to where "ati" as driver was specified.
If I do that now it gives an error message and XServer does not start up.
The only thing I can do is to set it to VGA, but that results in an 320x240 @8bit screen where I am not able to do anything sincerely at all...

Can anyone help? I am pretty much used to the fact that XServer does not work, but I do not know how to handle the present situation.
Since I am a total Linux beginner my knowledge is very rare as well.

I downloaded the newest ATI drivers already but if I go into the terminal and type in:
sudo ati-driver-installer-8.25.18-x86.run
all I get is an error message that says that the command is not there.

Did I do something wrong?
what would be the proper command to get the driver install to work?
and is there another way that I can get it to work over the text based console and not gnome? - Because I don't see very much in gnome so far.

(I also downloaded the rpms fglrx_4_3_0-8.25.18-1.i386.rpm)
Thanks for you help, in advance
Florian

---

### Post by franestepona on 2006-06-05
Hey! This is how I get to work the drivers, I'm quite new as well, i took it from one albenian website or something like that, but works perfectly, just follow the steps:

sudo -s
Password:
apt-get install module-assistant build-essential
apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

Nëse kemi pako të vjetra, ekzistuese fglrx, i fshijmë:

rm /usr/src/fglrx-kernel*.deb
rm -fr /usr/src/modules/fglrx

Tani jemi gati.

Krijojmë kartelën ku do të shkarkojmë drivers zyrtarë të ATI:

cd /usr/src
mkdir ATI
cd ATI
wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)
chmod +x ati-driver-installer-8.24.8-x86.run

Krijojmë pakot .deb, por në vend të Debian/Sid, përdorim Ubuntu/Dapper:

./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper

Dy minuta dhe gjithçka është gati për instalim

Instalojmë pakot që na nevoiten:
dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb
dpkg -i fglrx-control_8.24.8-1_i386.deb

Kompilojmë modulin për kernel në funksion:

module-assistant prepare,update
module-assistant build,install fglrx

Një tjetër minut akoma, dhe moduli konfigurohet dhe shtohet automatikisht në kernel.

Shënim: Për çdo upgrade të kernel, do t'ju duhet të rikompiloni modulin fglrx.

Përditësojmë konfigurimin e xorg:

aticonfig --initial
aticonfig --overlay-type=Xv

Rinisim kompjuterin:

shutdown -r now

Gjithçka në rregull mbas nisjes?

Kontrollojmë:

fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 SE Generic
OpenGL version string: 2.0.5755 (8.24.8)

After the installation of ATI control panel u can update it and the icon suddendly dissapear, if that happend run fireglcontrolpanel whenever u need the ATI control panel.

Hope this help.

---

### Post by sweeper on 2006-06-05
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29)

Don't know if that will suit your card but it worked for my 9800 pro.

---

### Post by joshrobinson on 2006-06-05
[QUOTE=franestepona]Hey! [/QUOTE]

that wget command is for the old ati driver, well the last version if it.. the new one is 8.25.18... although i did have better install with the last version and running xgl

ive been looking for a download of that file.. so thanks for the link!

---

### Post by Kilz on 2006-06-05
[QUOTE=joshrobinson]that wget command is for the old ati driver, well the last version if it.. the new one is 8.25.18... although i did have better install with the last version and running xgl

ive been looking for a download of that file.. so thanks for the link![/QUOTE]

The newest driver has problems , you may want to use the old ones. I had xgl running with 8.24.8 before, I upgraded to 8.25.18 and had to reformat and reinstall.

---

### Post by joshrobinson on 2006-06-05
[QUOTE=Kilz]The newest driver has problems , you may want to use the old ones. I had xgl running with 8.24.8 before, I upgraded to 8.25.18 and had to reformat and reinstall.[/QUOTE]

yeah the new ones junked my xgl.. so ive been looking around to find that file.. i had a .deb of it but i formatted and forgot to back it up like a moron.. so ill set up xgl later.. at least i know others are having problems with the new driver and xgl. so its not just me doing something stupid

---

### Post by sweeper on 2006-06-05
Doing it the way I linked to gets the 8.25.18 version too, is there anywhere I can get the 8.24.8?

Nevermind lol, I see it now.

---

### Post by franestepona on 2006-06-05
I installed the old ones and then updated to the new ones. I have the 8.24.8 running now and the only issue i had so far is the change of the name of the ATI control panel program, but i solved it as i say in the post.

---

### Post by joshrobinson on 2006-06-05
[QUOTE=sweeper]Doing it the way I linked to gets the 8.25.18 version too, is there anywhere I can get the 8.24.8?

Nevermind lol, I see it now.[/QUOTE]

your edit beat me to it :-p

thanks for the link to the older driver franestepona, been looking for it

---

### Post by sweeper on 2006-06-05
Just tried to install the older version, now I get this

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by franestepona on 2006-06-05
[QUOTE=sweeper]Just tried to install the older version, now I get this

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/QUOTE]

Back to no ATI drivers, which steps did you follow? Did you restart afterwards?

---

### Post by franestepona on 2006-06-05
By the way, is anyone of you have success with dual screen please let me know how, I have a headache with that :S

---

### Post by sweeper on 2006-06-05
I did what you did but maybe I should have uninstalled the others first?

---

### Post by franestepona on 2006-06-05
[QUOTE=sweeper]I did what you did but maybe I should have uninstalled the others first?[/QUOTE]
I'm not sure what is wrong. I have check the website from which you did it first time and it didn't work for me. Compare my /etc/X11/xorg.conf with yours. Make a copy of it first if you decide to change something.
```

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "es"
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

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by sweeper on 2006-06-05
The way I did it the first time isn't working for me now either, I will try what you are suggesting but I am a bit of a noob :)

---

### Post by franestepona on 2006-06-05
I forgot to say that you can force xorg to use the ATI drivers modifiyin the section device:

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

That worked for me with Ubuntu 5.10, but the same steps messed up the xorg file in my friend's computer. If you dont find a better solution you can try that.
Good luck.

---

### Post by sweeper on 2006-06-05
[QUOTE=franestepona]I forgot to say that you can force xorg to use the ATI drivers modifiyin the section device:

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

That worked for me with Ubuntu 5.10, but the same steps messed up the xorg file in my friend's computer. If you dont find a better solution you can try that.
Good luck.[/QUOTE]


Thanks mate but I fixed it :)

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5755 (8.24.8)

For some reason it wasn't downloading the .run file to the ATI folder so I just moved it in there and it worked :)
I dunno why the method I used first from wiki wouldn't work when it worked the first tho.

---

### Post by Flavian on 2006-06-06
Thanks very much guys!
I finally made it.
All I did was:
setting the driver in the xorg.conf to "vga", setting default bitrate to "8"
and started ubuntu with GREAT graphics :D I finally managed it to install the newest ATI driver with sudo ./ati...run
and then restarted.
aticonfig did not work though. - So I backuped my xorg.conf and than replaced it with franestepona's (thanks for postint yours, it helped me A LOT!
And finally TADA, it worked...
looks all nice and smoothy now, awesome.

Thanks to all of you!
Flo

---

