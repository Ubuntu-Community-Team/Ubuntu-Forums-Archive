---
title: "my first hour ever with Ubuntu"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by DynamicJ on 2007-03-14
ok, so far so good.  installation was fine.  

I have searched around about getting a proper resolution for my 19" Widescreen monitor... Hanns-G HW191D.  I used to run 1440X900 on winXP, and now I am stuck in 1024X768.  

I am COMPLETELY new to this, and I have seen where people are saying "edit your xorg.conf"  I do not even know what this is... :( I know thats bad, but I do want to learn, and would appreciate any help... if someone could kinda guide me through this, it would be the first step in making this a great thing for me.

thanks,

AJ

---

### Post by dhughes on 2007-03-14
xorg.conf is a text file that determines various things but most of all it is where you specify such things as your video card model, refresh rates and all the resolutions your card is capable of and what your monitor can show.

 What kind of video card do you have? I highly recommend a small application called Envy. You download it, click on it and it will do all the work of setting up pretty much everything to do with your video card and monitor.

 It's only for Nvidia or ATI cards, just follow the instructions they are pretty clear even for a beginnger. The Terminal can be found at Applications>Accessories>Terminal. Just copy and paste the text into Terminal and press the Enter key after each line of code you see.

 [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by siciliancasanova on 2007-03-14
This will tell you your video card:

```
lspci
```

---

### Post by DynamicJ on 2007-03-14
```
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV37GL [Quadro FX 330/GeForce PCX 5300] (rev a2)
02:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:02.0 Communication controller: Intel Corporation 536EP Data Fax Modem
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)

```

ok, thats what it is telling me... I'm going to download envy and see if this helps.

---

### Post by swoskow on 2007-03-14
The easy way - go to preferences>screen resolution and a dialog box comes up.  You can change the resolution to another option and keep trying one until you get what you like  Once you find the resolution you like then you can check the box that says "make default for this computer".

(note that when you change the resolution another dialog box will come up and ask if you want to make this the resolution to use from now on or something like that).  You can say yes or no it doesn't matter because you can always go back and change it by repeating the procedure above.)

Hope this helps

---

### Post by siciliancasanova on 2007-03-14
The thing is swoskow is that, that method doesn't work all the time.  See my post [here]("http://www.ubuntuforums.org/showthread.php?t=384569"). Search for "screen resolution" and you will see it's not just me.

Your video card is here:
```
01:00.0 VGA compatible controller: nVidia Corporation NV37GL [Quadro FX 330/GeForce PCX 5300] (rev a2)
```

If that envy program doesn't work, we can walk you through on the xorg configuration.

---

### Post by undertakingyou on 2007-03-14
> **DynamicJ said:**
> ```
00:00.0 Host bridge: Intel Corporation 
ok, thats what it is telling me... I'm going to download envy and see if this helps.

You could also just install the drivers yourself.
I think it is [CODE]nvidia-glx
```

---

### Post by swoskow on 2007-03-14
OK - I am new myself to Ubuntu (just got my install working with Ubuntu, Samba, Raid/LVM).  I am sure you are right but he might as well start simple see if that works and if not go from there.

---

### Post by DynamicJ on 2007-03-14
k, drivers installed.  everything was fine through Envy.  thanks for the link, btw.

now, still no option for 1440x900.... i went to preferences/screen resolution... no diologue boxes... ever.

what's next?

---

### Post by siciliancasanova on 2007-03-14
Run ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by MetalMusicAddict on 2007-03-14
Do what  siciliancasanova said and post the text in a post here. Ill whip up what you need.

---

### Post by DynamicJ on 2007-03-14
woohoo!!  fixed!

went Applications/system tools/nvidia settings

changed to 1440X900 50hz refresh

done!

looks great

---

### Post by MetalMusicAddict on 2007-03-14
50hz is low. If you post your current xorg here I can probably get you better.

---

### Post by siciliancasanova on 2007-03-14
Good to hear, I would recommend (at least this is what I do) keep a folder full of some notepad files, and name them like "Xorg Configuration" and such and paste the steps we gave you in case you ever run into a problem again, you don't need to wait 2 hours on the forums to get your problem fixed, you can do it in 2 minutes yourself.  :)  Glad to see your problem fixed.

---

### Post by siciliancasanova on 2007-03-14
> **MetalMusicAddict said:**
> 50hz is low. If you post your current xorg here I can probably get you better.

I agree, your eyes are going to be hurting.  Oh and MetalMusicAddict, I need you to look at this post, no one has seemed to help me out and you seem like you might be able to... [X-Server to Screen Resolution]("http://ubuntuforums.org/showthread.php?t=384569")

---

### Post by tribaal on 2007-03-14
> Good to hear, I would recommend (at least this is what I do) keep a folder full of some notepad files, and name them like "Xorg Configuration" and such and paste the steps we gave you in case you ever run into a problem again, you don't need to wait 2 hours on the forums to get your problem fixed, you can do it in 2 minutes yourself.  Glad to see your problem fixed.

Even better - use tomboy to store your "text files". Layout is simplified, and you can search all your notes easily :)
Once I tried tomboy for  "random stuff" gathering I never looked back :)

- trib

---

### Post by MetalMusicAddict on 2007-03-14
Well in any case try this. All the resolutions in the config are 16:10 resolutions. You *should* get them all @60hz if you monitor supports the res. Be sure to change the "BusID" in this config to match yours in your config.

```
[SIZE="1"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation GeForce PCX 5300"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
        Option          "RandRRotation" "on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
    	HorizSync       30.0 - 81.0
    	VertRefresh     56.0 - 76.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation GeForce PCX 5300"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1050" "1440x900" "1280x800" "960x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
         Option  "Composite" "Enable"
EndSection[/SIZE]
```

---

### Post by siciliancasanova on 2007-03-14
> **tribaal said:**
> Even better - use tomboy to store your "text files". Layout is simplified, and you can search all your notes easily :)
Once I tried tomboy for your "random stuff" gathering I never looked back :)

- trib

I will look into that, thanks :)

---

### Post by DynamicJ on 2007-03-14
k, i got it bumped up to 60hz..

how do I show you my xorg?

---

### Post by siciliancasanova on 2007-03-14
> **DynamicJ said:**
> k, i got it bumped up to 60hz..

how do I show you my xorg?

You need to input this:

```
sudo gedit /etc/X11/xorg.conf
```

Copy and paste the output here

---

### Post by DynamicJ on 2007-03-14
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

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
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV37GL [Quadro FX 330/GeForce PCX 5300]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV37GL [Quadro FX 330/GeForce PCX 5300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by ljpm on 2007-03-14
You may need to enter the correct HorizSync and VertRefresh values for your monitor.

Look them up in the manual (or google if you don't have the manual).

your values seem to be a default.

---

### Post by siciliancasanova on 2007-03-14
Also need to add your screen res in this section, in line with the other resolutions...

```
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
```

---

