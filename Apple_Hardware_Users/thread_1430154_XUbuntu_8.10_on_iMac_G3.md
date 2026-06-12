---
title: "XUbuntu 8.10 on iMac G3"
date: 2010-03-15
forum: Apple Hardware Users
---

### Post by mlthmp on 2010-03-15
Had posted this in the starters area, but decided it may go better here.

Hey everyone! I am having a problem getting XUbuntu 8.10 to run on my G3. The funny thing is just yesterday Ubuntu 8.04 was working.. decided to move to XUbuntu instead (lighter load on system resources) and I haven't been able to get it going yet.

Right now it'll load into "low-graphics mode" but nothing else. I have tried the same xorg.conf settings I used to make Ubuntu 8.04 work with no luck. I have tried EVERY example I can find here, and on Google and everyone of them gives me a different error when X starts (IE, I've seen "(EE) Unable to find a valid frameratebuffer device" and "(EE) FBDEV(0): FBIOPUT_VSCREENINFO succeeded but modified mode" so many times I have a headache! lol)

So here is where I stand right now. After hours of tinkering with the xorg.conf file I have ran the "dpkg-reconfigure -phigh xserver-xorg" command and have a fresh xorg file.

For some reason I am not able to load firefox or anything on the system (I am gussing its because of the low-graph mode?) so I am making all my edits to the xorg file by hand. 

Anyway, here is my new (fresh) file typed out. Can anyone give me some suggestions here?

Section "Device"
Identifier "Configured Video Device"
EndSecton

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Also, this is a slot-loader (Snow) 600mhz 256MB ram.. if that matters at all.

Thanks!

---

### Post by linuxopjemac on 2010-03-15
with so little RAM you might have a problem indeed, I would go for 512 Mb minimum, but that's up to you.

For your type of xorg.conf file copy and paste this one ([here ]("http://mac.linux.be/content/cross-distribution-issues")you will find them all)

```
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "dbe"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Driver "ati"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
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
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

---

### Post by mlthmp on 2010-03-15
I type all that in, and I get,

"Problem parsing the config file"
"Error paring the config file"

I know that likely means there is a typo somewhere, but I do not know where. I have retyped the entire thing twice, making sure of all the spelling and caps are right.. I have tried removing the "Files" and "Module" sections, and all but the Display for 24 bit (I found online that these areas are most likely to contain the typos) and still the parsing errors. I am unable to open FireFox (or most other programs) on the iMac right now, as I said above I am hoping that's just because of the low-graphics mode. That's why I am having to do this all by hand =(

Since I am already having trouble.. I am taking the opportunity to download Xubuntu 9.04 for PPC while I am tinkering with this. If I do not have this straightened out by the times it's done downloading I am going to go ahead and throw 9.04 on instead of 8.10 (9.10 was larger than my CD!) 

I figure I will have the same issue with 9.04 as I am with 8.10, but at least it'll be a newer version.. lol.

---

### Post by linuxopjemac on 2010-03-15
You will have the same troubles with 9.04! Try to  tackle the problem now, it's better.

You have to use an editor like nano or gedit as root, otherwise you cannot save. 

```
sudo gedit /etc/X11/xorg.conf
```

then just delete what you have and paste the lines I gave you above in that editor. Save and exit. You should not type all that stuff!!!

---

### Post by mlthmp on 2010-03-15
Ive been using nano to make the edits so far. After I open a terminal (ctrl-option-F1) I login with my username / pw.. type sudo -s for root access.. and use the command nano /etc/X11/xorg.conf this is where I have been editing from.

The problem is (why I am having to type it all by hand) is I cannot get firefox (or most other programs) to open on the machine. I click the icon and get the mouse icon that it's loading.. and then nothing happens.. I don't have a way to copy it onto the linux machine (iMac) so I am having to view the lines on this one (windows 7) and type it all out by hand on the other =(

I've even tried copying it to a txt file.. burned to a CD but the iMac couldn't mount the drive to open the file, lol.

---

### Post by linuxopjemac on 2010-03-15
use a program like lynx (text based browser)
```
sudo apt-get install lynx
```

you can then copy and paste I think

then 
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by linuxopjemac on 2010-03-15
also make sure you have a console mouse:
```
sudo apt-get install gpm
```

[http://www.gentoo.org/doc/en/gpm.xml](http://www.gentoo.org/doc/en/gpm.xml)

---

### Post by mlthmp on 2010-03-15
linuxopjemac.. thank you for all your help =)

Ok, so far I have installed lynx, and gpm. I have also installed XUbuntu 9.04 already. I decided I may as well go ahead and install the slightly newer version since I was already having trouble.

When the system boots alone, it freezes and the screen goes blank. When I booted with the "Linux video=ofonly" command XUbuntu started in low-graphics mode, and I got the following errors.

Failed to load module "freetype" (module does not exist)
Failed to load module "type1" (module does not exist)
No drivers available.

So I went into xorg.conf and and made the following edits.

#Load "freetype"
#Load "type1"

Rebooted and using the ofonly command, and I got low-graphics mode again, this time with only one error.

(EE) No drivers available.

Am I getting any closer? =(

---

### Post by mlthmp on 2010-03-15
Alright, well at the moment I am at an impasse it seems.

I have edited the yaboot loader to append the video=ofonly nosplash options to keep the system from hanging on boot. However, the only way I can get the GUI to start is by reconfiguring the xorg.conf file and using a very basic setup. 

For example, here is all mine reads at the moment.

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


Very basic, and has no advanced optins. However the desktop enviroment loads. Matter of fact I am posting from within Xubuntu 9.04 on my iMac right now. However, the resoultion is HORRIBLE. I do not have many colors (256 AT BEST) and no matter what type of edits I make to the xorg.conf file (for example, if I use the suggested file from above) it gives me the low-graphics error. 

I feel I am close to a solution, but my knolodge of Linux is, well, as you cna likely tell very minimal. Any suggestions on where to go from here?

At the moment I have this machine running updates.. When I had 8.10 installed NOTHING would load. So far everything is loading here in 9.04, but the colors are bad =(

---

### Post by linuxopjemac on 2010-03-16
I would begin with installing more RAM...

---

### Post by oswaldkelso on 2010-03-16
as root:

cd /etc/X11

cp xorg.conf    xorg.conf-bu 

wget [http://debe17.com/imac-ppc-slot-loader-500_600_700-xorg.conf](http://debe17.com/imac-ppc-slot-loader-500_600_700-xorg.conf)

cp imac-ppc-slot-loader-500_600_700-xorg    xorg.conf

reboot

Ubuntu is getting abit bloated for these older machines, once you're more familiar lighten up your system

---

### Post by mlthmp on 2010-03-16
> **linuxopjemac said:**
> I would begin with installing more RAM...

That's on the agenda, but I would like to have a working system in place first. I have a second iMac with less memory and a slower processor that flies through Mac OS X 10.3.. so I would have thought for sure this one (faster processor, more memory) would be able to handle XUbuntu.. at least somewhat =(

> **oswaldkelso said:**
> as root:

cd /etc/X11

cp xorg.conf    xorg.conf-bu 

wget [http://debe17.com/imac-ppc-slot-loader-500_600_700-xorg.conf](http://debe17.com/imac-ppc-slot-loader-500_600_700-xorg.conf)

cp imac-ppc-slot-loader-500_600_700-xorg    xorg.conf

reboot

Ubuntu is getting abit bloated for these older machines, once you're more familiar lighten up your system

Done, however now I am getting two error messages.

(EE) failed to load module "freetype" (module does not exist, 0)
(EE) No drivers available.

---

### Post by linuxopjemac on 2010-03-16
no drivers available I find disturbing...your Mac has a Rage 128 Ultra card, so you need the ATI driver.

You need to install the ati driver, otherwise, the driver can't be found:
```

sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-r128
```

to fix this freetype thing, I would just comment it out, you don't really need it, like this:
```
# Load "freetype"

```

---

### Post by linuxopjemac on 2010-03-16
If that does not work, we would like to see this:

```
cat /var/log/Xorg.0.log
```

---

### Post by mlthmp on 2010-03-16
[FONT=monospace]Just want to say thanks again to everyone for their help so far with this! I have ran the two commands given above, and have posted their output below. Also, I had to again go back to a standard xorg.conf file in order to load the desktop so I could copy/paste the blow outputs. I do not know if that would make a difference in the readouts or not. However it wouldn't let me load the desktop in low-graphics mode =(

sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-r128
brings up,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-ati is already the newest version.
xserver-xorg-video-r128 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 191 not upgraded.


cat /var/log/Xorg.0.log 
brings up,

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ubuntu 2.6.28-6-powerpc #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 ppc
Build Date: 09 April 2009  02:10:13AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@ross.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 16 16:45:14 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x1e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(II) Open APM successful
(II) System resource ranges:
    [0] -1    2    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    2    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    2    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    2    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    1    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    1    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    1    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    1    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    2    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [13] -1    2    0x00000000 - 0x00000000 (0x1) IX[B]
    [14] -1    1    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    1    0x00000000 - 0x00000000 (0x1) IX[B]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
Primary device is not PCI
(==) Matched fbdev for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) FBDEV: driver for framebuffer: fbdev
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(II) FBDEV(0): using default device
(II) Running in FRAMEBUFFER Mode
(II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 8/8
(==) FBDEV(0): Depth 8, (==) framebuffer bpp 8
(==) FBDEV(0): Default visual is PseudoColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: OFfb ATY,Rage12 (video memory: 768kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
(**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 94.0 kHz, 116.3 Hz
(II) FBDEV(0): Modeline "current"x0.0  100.00  1024 1040 1048 1064  768 784 792 808 -hsync -vsync -csync (94.0 kHz)
(==) FBDEV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) FBDEV(0): Backing store disabled
(II) FBDEV(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Mouseemu virtual keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event5"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Mouseemu virtual keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Mouseemu virtual keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Mouseemu virtual keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Alps Electric M2452
(**) Alps Electric M2452: always reports core events
(**) Alps Electric M2452: Device: "/dev/input/event3"
(II) Alps Electric M2452: Found keys
(II) Alps Electric M2452: Configuring as keyboard
(II) XINPUT: Adding extended input device "Alps Electric M2452" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Alps Electric M2452: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Alps Electric M2452: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Alps Electric M2452: xkb_layout: "us"
(II) config/hal: Adding input device Mouseemu virtual mouse
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event6"
(II) Mouseemu virtual mouse: Found 3 mouse buttons
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Configuring as mouse
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
(**) Mouseemu virtual mouse: (accel) filter chain progression: 2.00
(**) Mouseemu virtual mouse: (accel) filter stage 0: 20.00 ms
(**) Mouseemu virtual mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech Optical USB Mouse
(**) Logitech Optical USB Mouse: always reports core events
(**) Logitech Optical USB Mouse: Device: "/dev/input/event2"
(II) Logitech Optical USB Mouse: Found 3 mouse buttons
(II) Logitech Optical USB Mouse: Found x and y relative axes
(II) Logitech Optical USB Mouse: Configuring as mouse
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
(**) Logitech Optical USB Mouse: (accel) keeping acceleration scheme 1
(**) Logitech Optical USB Mouse: (accel) filter chain progression: 2.00
(**) Logitech Optical USB Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech Optical USB Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Mouseemu virtual keyboard
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event5"
(WW) Mouseemu virtual keyboard: device file already in use. Ignoring.
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Mouseemu virtual keyboard"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Mouseemu virtual mouse
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event6"
(WW) Mouseemu virtual mouse: device file already in use. Ignoring.
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Mouseemu virtual mouse"
(EE) config/hal: NewInputDeviceRequest failed (8)


[/FONT]

---

### Post by linuxopjemac on 2010-03-17
I want to see the output of your X with the config file I gave you, it has another log name if you go to a new config file, check it out, they have different names under /var/log/Xorg....The one you show me now is the one with a config file of your own, I am not interested in that.

find me the one with ATI.

---

### Post by linuxopjemac on 2010-03-17
By the way, what is the Xorg.conf file you use to have this log file ? I'd be interested to know what Xorg.conf file you use as a fall back. Something with a framebuffer device ?

---

### Post by linuxopjemac on 2010-03-17
I found another xorg.conf file [here]("http://forums.macrumors.com/showthread.php?t=662667") (post #11):

> ```

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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#	Load	"ic2"
	Load	"bitmap"
#	Load	"ddc"
	Disable	"dri"
	Load	"extmod"
	Load	"freetype"
	Disable	"glx"
	Load	"int10"
#	Load	"type1"
	Load	"vbe"
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
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZaxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 RL/VR AGP"
	Driver		"r128"
	Option		"UseFBDev"	"false"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	58-62
	VertRefresh	75-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 RL/VR AGP"
	Monitor		"iMac"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"		
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection 
```

---

### Post by linuxopjemac on 2010-03-17
For later, we can try to get DRI working with [this post]("http://forums.opensuse.org/archives/sf-archives/archives-ppc/333823-i-found-how-make-dri-work-imac-g3-r128-suse-10-2-a.html").

---

### Post by llamabr on 2010-03-17
to change the subject a bit, ubuntu gave up on supporting the ppc architecture a few releases ago, and so even if you get this working, things on your old ppc machine will just go neglected by ubuntu.

I run debian lenny on my ibook, and everything works right from a fresh install, including sound, graphics, airport.  For lower resources, i use wmaker, rather than gnome, or xfce (which is what you're after).  It's a bit slow, but it gets the job done.  I found it much easier than fighting with ubuntu

---

### Post by mlthmp on 2010-03-18
I would like to sincerely thank linuxopjemac, and oswaldkelso for their assistance in this matter. I became very flustered trying to get XUbuntu installed on this machine. Every possible edit I made to the xorg.conf file gave me new errors. 

Earlier this morning I gave up trying to install XUbuntu on this system, and reinstalled Ubuntu 8.04 without a lick of trouble. It installed fine, and took only two edits to the corg.conf file. However, it was very, VERY slow. I then tried Ubuntu 9.10 and believe it or not it installed fine also, but was slow (although not quite as slow as 8.04 was!) 

About two hours ago I noticed llamabr's suggestion about Debian. I decided to give it a shot as I have figured out I can always fall back on Ubuntu 8.05 or 9.10 if needed. Debian 5.04 installed in about 45 minutes, and this has been a wonderful experience so far. I did use the xorg file oswaldkelso linked to above ([http://debe17.com/imac-ppc-slot-loader-500_600_700-xorg.conf](http://debe17.com/imac-ppc-slot-loader-500_600_700-xorg.conf)) and everything is working like a dream. It's a little sluggish, but surprisingly faster than Ubuntu 8.04 or 9.10

I apologize for having been a burden to you guys these past couple of days, and appreciate all the suggestions and help you've offered! While I was not able to get Xubuntu installed like I had hoped, this experience had helped me learn quite a few linux commands I did not know before. I feel I have a bit better understanding of Linux now, and I appreciate that guys!

Mike,

---

### Post by linuxopjemac on 2010-03-18
I agree with llamabr that Debian is better. If people really insist on having Ubuntu, I try to help them to get Ubuntu on their machines. I only run Debian on my PPC hardware.

At least you learned something :) I am happy that it now finally works for you. Enjoy the ride. Another happy convert :)

To make your computer faster you can do two things:

1) Increase the amount of RAM
2) step down in GUI: KDE and Gnome use a lot of resources, there are many other GUI's which are less consuming (like fluxbox for example) Have a look at the link, it shows a few low RAM desktop managers, there are many more by the way. Google and you will find them. You can easily swith to such a desktop manager. Just install from the synaptic package manager and from the login GUI, you can set the session you like:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by oswaldkelso on 2010-03-18
Cool. If you have a good internet connection you might want to upgrade to Debian squeeze it's very stable even if it's the testing release. This will give you newer packages. At the expense of needing to up-date your system regularly.

In my experience the xfce/lxde [http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/powerpc/iso-cd/debian-testing-powerpc-xfce+lxde-CD-1.iso) install works very well on PPC if you want a little more speed a pure openbox-rox-fbpanel-tint2 is ace but needs a fair bit of tweaking and has a much steeper learning curve to get te best out of it.

The thing to remember about Debian, is it gives you a diamond but you have to polish it yourself.

---

### Post by linuxopjemac on 2010-03-18
> The thing to remember about Debian, is it gives you a diamond but you have to polish it yourself. 

Oswald, I like that one.

---

