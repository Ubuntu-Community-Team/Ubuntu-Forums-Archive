---
title: "iMac G3 ubuntu stuck in low-graphics mode"
date: 2010-06-22
forum: Apple Hardware Users
---

### Post by PSimpso on 2010-06-22
I have an iMac G3 (slot-loading, 400Mhz); I've successfully installed Ubuntu and Xubuntu 10.04 and earlier I installed Ubuntu 9.04. However, it's stuck in low-graphics mode.

And, ever since I did the **cmd + option + p + r** command the display shrunk a bit leaving some black space around the display (after following these instructions: [http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934))

Any ideas?

I'm trying to get this thing up and running as a basic internet machine.

---

### Post by linuxopjemac on 2010-06-23
ok, you have a terminal, give me the output of the following commands, paste them here in this thread:

```
cvt 1024 768
cvt 800 600
cvt 640 480
```

---

### Post by PSimpso on 2010-06-23
[B]cvt 1024 768:
[/B]
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync


[B]cvt 800 600:
[/B]
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync


[B]cvt 640 480:
[/B]
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync

---

### Post by linuxopjemac on 2010-06-24
Try this xorg.conf file. Tell me if it works. If it does not work, give me the output of:

```
sudo cat /var/log/Xorg.0.log
```


```
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "true"
Option "NoInt10" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00" 23.75 640 664 720 800 480 483 487 500 -hsync +vsync
Option "PreferredMode" "800x600_60.00"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by PSimpso on 2010-06-24
Am I supposed to copy and paste that second section into my xorg.conf file? I searched for the xorg.conf file and found the file named xorg.conf.failsafe

---

### Post by linuxopjemac on 2010-06-24
yes, you should take that whole code part into xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

then paste the lines there
then CTRL-x and "y" to save

---

### Post by PSimpso on 2010-06-24
Ok, I tried that second part as both the xorg.conf and xorg.conf.failsafe file and it didn't work.

Here is the output of "sudo cat /var/log/Xorg.0.log"


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-22-powerpc64-smp ppc Ubuntu
Current Operating System: Linux patrick-desktop 2.6.32-22-powerpc #36-Ubuntu Thu Jun 3 23:00:32 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash video=ofonly 
Build Date: 16 June 2010  09:45:48AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 24 22:01:55 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x101ebbe4
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:16:0) 1002:5052:1002:5052 ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded even though the default is to disable it.
(II) "record" will be loaded by default.
(II) "dri" will be loaded even though the default is to disable it.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched fbdev as autoconfigured driver 1
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) FBDEV: driver for framebuffer: fbdev
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) FBDEV(0): using default device
(II) Running in FRAMEBUFFER Mode
(==) FBDEV(0): Depth 8, (==) framebuffer bpp 8
(==) FBDEV(0): Default visual is PseudoColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: OFfb ATY,Rage12 (video memory: 768kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0):     mode "1024x768" test failed
(II) FBDEV(0):     mode "800x600" test failed
(II) FBDEV(0):     mode "640x480" test failed
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
(**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 94.0 kHz, 116.3 Hz
(II) FBDEV(0): Modeline "current"x0.0  100.00  1024 1040 1048 1064  768 784 792 808 -hsync -vsync -csync (94.0 kHz)
(==) FBDEV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) FBDEV(0): Backing store disabled
(==) FBDEV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device PowerMac Beep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Alps Electric Apple Extended USB Keyboard (/dev/input/event2)
(**) Alps Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Alps Electric Apple Extended USB Keyboard: always reports core events
(**) Alps Electric Apple Extended USB Keyboard: Device: "/dev/input/event2"
(II) Alps Electric Apple Extended USB Keyboard: Found keys
(II) Alps Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Alps Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-61EE7089AE8A96287C2B829E837E808A04504E84.xkm
(II) config/udev: Adding input device Alps Electric Apple Extended USB Keyboard (/dev/input/event3)
(**) Alps Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Alps Electric Apple Extended USB Keyboard: always reports core events
(**) Alps Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
(II) Alps Electric Apple Extended USB Keyboard: Found keys
(II) Alps Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Alps Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Fujitsu Takamisawa Component Apple Optical USB Mouse (/dev/input/event4)
(**) Fujitsu Takamisawa Component Apple Optical USB Mouse: Applying InputClass "evdev pointer catchall"
(**) Fujitsu Takamisawa Component Apple Optical USB Mouse: always reports core events
(**) Fujitsu Takamisawa Component Apple Optical USB Mouse: Device: "/dev/input/event4"
(II) Fujitsu Takamisawa Component Apple Optical USB Mouse: Found 1 mouse buttons
(II) Fujitsu Takamisawa Component Apple Optical USB Mouse: Found relative axes
(II) Fujitsu Takamisawa Component Apple Optical USB Mouse: Found x and y relative axes
(II) Fujitsu Takamisawa Component Apple Optical USB Mouse: Configuring as mouse
(**) Fujitsu Takamisawa Component Apple Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Fujitsu Takamisawa Component Apple Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Fujitsu Takamisawa Component Apple Optical USB Mouse" (type: MOUSE)
(II) Fujitsu Takamisawa Component Apple Optical USB Mouse: initialized for relative axes.
(II) config/udev: Adding input device Fujitsu Takamisawa Component Apple Optical USB Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PMU (/dev/input/event1)
(**) PMU: Applying InputClass "evdev keyboard catchall"
(**) PMU: always reports core events
(**) PMU: Device: "/dev/input/event1"
(II) PMU: Found keys
(II) PMU: Configuring as keyboard
(II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "mac"
(**) Option "xkb_options" "lv3:ralt_switch"

---

### Post by PSimpso on 2010-06-24
Ok, that's what I did. I would copy and paste it into the file, save it, and reopen it to make sure that it was actually saved (it was). Then I'd restart the computer, it still is in low-graphics mode and the xorg.conf file had reverted back to its original state.

---

### Post by linuxopjemac on 2010-06-25
strange strange, it borks at the keyboard. It looks similar to some other guy trying to get X working, he also has problems with the keyboard...I really don't know what to do about this.

[http://ubuntuforums.org/showthread.php?t=1511286&page=4](http://ubuntuforums.org/showthread.php?t=1511286&page=4)

It is getting harder and harder to get Ubuntu working on PPC machines it seems. I would opt for Karmic Koala or Debian Linux. I am out of options here...It looks like some kind of bug of evdev or so.

One more try:

Do as suggested [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/532114"):

install xserver-xorg-input-kbd_1.4.0-1_powerpc.deb from debian sid and add Option "AllowEmptyInput" "off" to your xorg.conf. Just add the following lines at the end of xorg.conf:


```
Section "ServerFlags"
Option "AllowEmptyInput" "off"
EndSection
```

Your whole xorg.conf file will look like this then:

```
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "true"
Option "NoInt10" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00" 23.75 640 664 720 800 480 483 487 500 -hsync +vsync
Option "PreferredMode" "800x600_60.00"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "ServerFlags"
Option "AllowEmptyInput" "off"
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by PSimpso on 2010-06-25
I'll try Karmic. I have no need be on the bleeding edge with such old hardware.  I did, however, have Ubuntu 9.04 installed previously and I was having the same low-graphics mode issue - but I didn't try any xorg.conf file editing. Is there any reason why I should use 9.10 over 9.04? Would 9.04 run any better?

You said something about the keyboard-would using a completely different USB keyboard do any good?

Also, am I out of luck with the black around the edges of the screen problem? Would I have to install Mac OS 9 to adjust the iMac's monitor?

---

### Post by linuxopjemac on 2010-06-26
Just try Karmic Koala (9.10). I think that it will work fine.

---

### Post by PSimpso on 2010-06-29
I installed 9.10 but now there's no xorg.conf file to be found.

I found something about using xvidtune to adjust the position and size of the screen. I need to look into it more.

---

### Post by PSimpso on 2010-06-30
Oh man, I finally got the colors to display correctly using this code for the xorg.conf file from 
[http://ubuntuforums.org/showthread.php?t=1169092&page=5](http://ubuntuforums.org/showthread.php?t=1169092&page=5)

```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection
```

I tried a different xorg.conf file; had to remove xserver-xorg so I could delete the old xorg.conf and xorg.conf.failsafe files. Then reinstalled xserver-xorg and created the new xorg.conf file from scratch.

Now I just have to get xvidtune working to adjust the screen!

---

### Post by linuxopjemac on 2010-06-30
Why don't you try the xorg.conf file I wrote for you ?

---

### Post by PSimpso on 2010-06-30
I actually did first and it didn't work. I could only boot to the terminal. But wait, is the second one you wrote different than the first? I think I only tried the first one.

Is there part of the code that just adjusts the screens position? If so, can I just use that part of it?

---

### Post by linuxopjemac on 2010-06-30
Just try the first one I gave you. If that does not work, my last idea is to delete the 
```
Option "UseFBDev" "true"
```
in the Device section

be sure to have the ati xserver xorg driver:
```
sudo apt-get install xserver-xorg-video-ati
```

---

### Post by PSimpso on 2010-07-06
I tried your xorg.conf file and the computer wouldn't boot bast the terminal.

I tried the xorg.conf settings found here and it booted in 24 bit color again.
[https://wiki.ubuntu.com/PowerPCFAQ#Video%20settings%20for%20G3%20iMac](https://wiki.ubuntu.com/PowerPCFAQ#Video%20settings%20for%20G3%20iMac)

And, it will now let me get into xvidtune - But, it won't let me make any changes. With my previous settings, it wouldn't even go into the xvid program.

I may just have to live with my off-center screen for now.

---

### Post by linuxopjemac on 2010-07-07
Can you post your working xorg.conf file please ?

---

### Post by PSimpso on 2010-07-10
My current xorg.conf file:

```
# xorg.conf (X.Org X Window System server configuration file)
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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 58-62
VertRefresh 75-117
#ModeLine "1024x768" 78.75 1024 1044 1140 1328 768 781 784 820 +hsync +vsync
#ModeLine "800x600" 62.40 800 821 901 1040 600 609 612 644 +hsync +vsync
#Modeline "640x480" 49.90 640 657 721 832 480 481 484 514 +hsync +vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24 
Modes "1024x768" "800x600" "640x480"
#Virtual 1024 768
EndSubSection
EndSection

Section "Module"
Disable "dri"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "CCEusecTimeout" "100000"
#Option "UseFBDev" "true"
EndSection

```

When I try to adjust anything using xvidtune it gives me this error:

"Sorry: You have requested a mode-line that is not possible, or not supported by your hardware configuration"

---

### Post by Xeekder on 2010-10-22
ABSOLUTE THANKS!!... FIRST xorg.conf working on summer 2001 imac snow!!!!!!! runnig 9.10 karmic.. thaks for posting what worked for you!

---

