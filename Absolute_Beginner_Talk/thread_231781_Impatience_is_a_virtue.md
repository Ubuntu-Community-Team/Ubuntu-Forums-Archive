---
title: "Impatience is a virtue???"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by sherpah on 2006-08-07
Hi All,

I know this has been covered before in other forums to some degree - but I have a specific problem with my laptop and my Intel 855GM onboard graphics card - and I think it must be related to my overall noobishness - though I have some broader experence with linux - (Red Hat pre Fedore, etc) I am shaking off the rust... here is my problem:

I have a fujitsu Lifebook P5010 subnotebook - and I am dualbooting Ubuntu. In order to install on a dualboot system with and keep my current bootloader intact (bootitng) I needed to install Ubuntu from the ALTERNATE INSTALL CD.

I Installed on expert mode to avoid putting GRUB on the MBR. I was successful, and after a base install of UBUNTU from the ALTERNATE CD, I then used SUDO APTITUDE command to install all the packages I thought I needed, including Xserver and GNOME. I then reboot, and Xserver and GNome works, I even used the little hack program to get widescreen enabled (1280x768 native on my P5010). But here is the main problem - I cannot run anything that requires 3d - specifically GLX. GLXGEARS and GLXINFO give me strange errors and wont work at all - see below.

Now I have read through hours of threads on the net and tried all kinds of stuff - including attempting to change kernels from a 386 to a 686 - but i don't think I need a 686 kernel. Also - when I boot in UBUNTU off the UBUNUT LIVE CD - GLX works perfectly - its just off of my install that it doesnt - so I know my hardware can support it on Ubuntu.

If I run GLXGEARS nothing happens, except this error message:

Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


If I run GLINFO I get this:

name of display: :0.0
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x21 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x22 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None

My Xorg.conf looks like this;
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
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
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
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

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection


--------------------------------
Uname -a:

Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux





Any advice is appreciated. I think I am missing something basic, like maybe a simlink to a lib file - but the problem is just over my head.

Thanks in advance.

---

### Post by Ziox on 2006-08-07
> **sherpah said:**
> Hi All,

I know this has been covered before in other forums to some degree - but I have a specific problem with my laptop and my Intel 855GM onboard graphics card - and I think it must be related to my overall noobishness - though I have some broader experence with linux - (Red Hat pre Fedore, etc) I am shaking off the rust... here is my problem:

I have a fujitsu Lifebook P5010 subnotebook - and I am dualbooting Ubuntu. In order to install on a dualboot system with and keep my current bootloader intact (bootitng) I needed to install Ubuntu from the ALTERNATE INSTALL CD.

I Installed on expert mode to avoid putting GRUB on the MBR. I was successful, and after a base install of UBUNTU from the ALTERNATE CD, I then used SUDO APTITUDE command to install all the packages I thought I needed, including Xserver and GNOME. I then reboot, and Xserver and GNome works, I even used the little hack program to get widescreen enabled (1280x768 native on my P5010). But here is the main problem - I cannot run anything that requires 3d - specifically GLX. GLXGEARS and GLXINFO give me strange errors and wont work at all - see below.

Now I have read through hours of threads on the net and tried all kinds of stuff - including attempting to change kernels from a 386 to a 686 - but i don't think I need a 686 kernel. Also - when I boot in UBUNTU off the UBUNUT LIVE CD - GLX works perfectly - its just off of my install that it doesnt - so I know my hardware can support it on Ubuntu.

If I run GLXGEARS nothing happens, except this error message:

Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


If I run GLINFO I get this:

name of display: :0.0
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x21 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x22 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None

My Xorg.conf looks like this;
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
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
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
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

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection


--------------------------------
Uname -a:

Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux





Any advice is appreciated. I think I am missing something basic, like maybe a simlink to a lib file - but the problem is just over my head.

Thanks in advance.

I guess you can try to let xorg to reconfigure itself through this command:

sudo dpkg-reconfigure xserver-xorg

and to check for 3d acceleration use this command:

glxinfo | grep rendering

if it works, then it'll return

direct rendering: yes

if it doesn't work, then i'll return

driect rendering: no

hopefully this helps.

---

### Post by sherpah on 2006-08-07
Ziox,

Thanks for the suggestion - I tried to reconfigure - but it didnt work - in fact, Xserver has now limited me to 640x480 resolution - and still No 3d support whatsoever. I still get the same error message when I run GLXINFO. 3d is just not working. Any other thoughts?

Thanks

---

### Post by Upochapo on 2006-08-07
hmmm...does your xserver generate any error files/logs? if it does, maybe there is a clue in there?

---

### Post by Ziox on 2006-08-07
> **Upochapo said:**
> hmmm...does your xserver generate any error files/logs? if it does, maybe there is a clue in there?

ahh..yes, that reminds me, the xorg log file is located at:

/var/log/Xorg.0.log

it is a huge file that gets created anew when a X server begins, so yes, that file may provide some answers to your problem...

---

### Post by Upochapo on 2006-08-07
i also caught the little part about the "hack"...now, when u ran the live cd did you do your hack?  did you try to see if you had 3d acceleration before you tried your hack after your installation?  if not, maybe it something has to do with that too.  

upo.

---

### Post by sherpah on 2006-08-07
Hi all,

THanks for the continued help - this problem is driving me nuts. As to the point about the hack program - At the moment, I do not even have it running, so it is not a variable - I have since resinstalled Ubuntu from the Alternate CD cleanly and not used that hack to make sure it was not affecting anything.

As far as the Xorg.log file - I have looked through it and have found the only area in the log that has some errors in it... they all seem to surround VESA ---- please take a look:

(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 855GM
(--) I810(0): Chipset: "852GM/855GM"
(--) I810(0): Linear framebuffer at 0xD8000000
(--) I810(0): IO registers at addr 0xD0000000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): Kernel reported 110080 total, 1 used
(II) I810(0): Checking Available AGP Memory: 440316 kB available (total 440320 kB, used 4 kB)
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Tweak BIOS image to 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2878
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
              If you encounter this problem please add
                 Option "DisplayInfo" "FALSE"
              to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (800,600)(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (800,600)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present:
FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1280,768)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE,
size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Size of device LFP (local flat panel) is 1280 x 768
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0):   LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1280 x 768
(==) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1280x768
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(--) I810(0): A non-CRT device is attached to pipe B.
        No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte


Any leads from this? Thanks again

---

### Post by Upochapo on 2006-08-08
i googled a little bit, and i can't recall too well. I read about i830 driver? for your particular graphics card. is that an option when configuring xserver?  if not also try this and i completely forgot about this.  change your default depth to 16.  Not 24.  I had an intel that would not do 3d acceleration in 24 bit mode.  only 16...it's worth a shot.

edit:  i noticed that you are using the i810 driver.  check to see if there is an i830.  because, if i recall, correctly, i810 has limited 3d acceleration, ie 16 bit color depth.

---

### Post by sherpah on 2006-08-08
I checked into your theory about 16bit color depth....

I reconfigured xserver in 16bit - and still, same GLXINFO error as above - simply no GLX enabled, no 3d. So its not that - but when I do reconfigure the Xserver - the only option I have is for an i810 driver. I can also tell you that my video card is an onboard INTEL855/gme - and it is the kind of vcard that shares system Ram - but 16bit trick did not solve the problem

any other ideas? Again - I know it CAN work, because when I boot off the UBUNTU LIVE CD, GLXGEARS and GLXINFO works perfectly.

I think I am missing somethings fundamental, like a bad path, or link or missing library.

Any thoughts are very appreciated.

---

### Post by Upochapo on 2006-08-08
dang :sad: ... i'm kinda stumped on this as well...wonder why the alt cd isn't configuring it correctly for you...at this point i'm stumped...the only thing i can do is help you research and find some information...i will look myself until someone comes along who may actually knows what the problem is.  i apologize as i'm still fairly new to ubuntu.  i will keep looking and see if i come across anything and use your posts for reference. *sigh*...lemme see what i can find out.

sorry, i couldn't give you a straight answer to your problem.

---

### Post by Upochapo on 2006-08-08
wow.  you weren't joking when you said it was hard to find someone else with the same problem...i have read several suggestions on what you may want to try.  none of which look pretty in my opinion.  I know that your graphics card need agpgart because of sharing system memory.  At this stage i would feel uncomfortable giving out advice as I do not want you to mess up your system.  It definitely looks like glx isn't getting loaded but I wouldn't know where to begin.  I know that the i810 driver is fine as was in livecd.  I wonder if it's possible to read the xorg.conf file that is generated by the live cd?  that's is something i don't know.  I would assume it generates some kind of file in ram somewhere.  

Well, it is late here.  I will check back tomorrow to see if anyone was able to fix ur problem.  I apologize, in advance, if you feel that i am wasting your time.  Take care.

Upo.

---

### Post by Paradoxdruid on 2006-08-08
I'm having the same, or a very similar problem, with my i810 driver, which I detailed here:  [http://ubuntuforums.org/showthread.php?t=231901](http://ubuntuforums.org/showthread.php?t=231901)

Just to collect advice together:

I was told to try ```
sudo ln -s /usr/lib/dri/ /usr/X11R6/lib/modules/dri
```
which didn't help.

Also, I was told that the BIOS frequently reports the video RAM as too low for 3d, so my xorg.conf has "VideoRam    65536" in the graphics card area.  No luck.

Lastly, I saw in some thread that people are saying Xorg 6.8 worked, but 7.0 and 7.1 broke something...  not sure, and I don't know how to downgrade to test that.

Trying a LiveCD is a good next step--  I'd hate to reformat and start over, but if that worked for my media PC, it's doable.

Beyond that, I'm at a loss--  the driver is in my kernel modules, the xorg.conf is set-up correctly, but my /var/log/Xorg.0.log reports ```
I810(0): Direct Rendering: Failed
```.

Here's hoping something comes along!

---

### Post by Ziox on 2006-08-08
> **sherpah said:**
> Hi all,

THanks for the continued help - this problem is driving me nuts. As to the point about the hack program - At the moment, I do not even have it running, so it is not a variable - I have since resinstalled Ubuntu from the Alternate CD cleanly and not used that hack to make sure it was not affecting anything.

As far as the Xorg.log file - I have looked through it and have found the only area in the log that has some errors in it... they all seem to surround VESA ---- please take a look:

(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 855GM
(--) I810(0): Chipset: "852GM/855GM"
(--) I810(0): Linear framebuffer at 0xD8000000
(--) I810(0): IO registers at addr 0xD0000000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): Kernel reported 110080 total, 1 used
(II) I810(0): Checking Available AGP Memory: 440316 kB available (total 440320 kB, used 4 kB)
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Tweak BIOS image to 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2878
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
              If you encounter this problem please add
                 Option "DisplayInfo" "FALSE"
              to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (800,600)(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (800,600)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present:
FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1280,768)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE,
size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Size of device LFP (local flat panel) is 1280 x 768
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0):   LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1280 x 768
(==) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1280x768
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(--) I810(0): A non-CRT device is attached to pipe B.
        No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte


Any leads from this? Thanks again

From what I see with this part of the log file, there aren't any errors really.  though, if the system is using the "vesa" driver, then most likely 3D acceleration cannot be enabled...but try to either post or attach the full Xorg.0.log file...

---

### Post by darrenm on 2006-08-08
Well from this:
> (II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): Kernel reported 110080 total, 1 used
(II) I810(0): Checking Available AGP Memory: 440316 kB available (total 440320 kB, used 4 kB)
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
It seems that the initial shared memory size is 8MB and the driver is trying to up that manually but the VGA BIOS doesn't have the function implemented.

Having absolutely no experience with the onboard Intel VGA in Linux I can't really suggest anything apart from trying to use a more specific driver. In fact there seems to be one exactly for your chipset on Intel [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

---

### Post by sherpah on 2006-08-08
I am going to try the new Intel driver - I have downloaded it and untarred. Does anyone know how to properly install though? The README only gives instructiosn for SUSE linux. I have no idea how to get it installed. I appreciate any help, thanks.

---

### Post by darrenm on 2006-08-08
Seems to be as simple as:

```
tar zxvf i915*
sudo sh install.sh
```

and follow through the installer. I got compile errors on mine though...

May be worth an email to intel support to ask for a driver that will compile with your kernel headers.

---

### Post by sherpah on 2006-08-08
Darren,

I got the same compile errors - and I also found this website - which from what I can tell maintains intel graphics drivers that support my chip - would you mind verifying this for me - as I have downloaded and installed these drivers - but i cannot seem to get them to take - or at least it is no obvious to me that they have taken as glxinfo still returns the same error


The website with the drivers is:\ freedesktop.org


take a look at this link - from ubuntu forums - and see what I mean. 

[http://www.ubuntuforums.org/showthread.php?t=7200](http://www.ubuntuforums.org/showthread.php?t=7200)

this shows how to get 3d runing for ati - but the freedesktop website also has the intel drivers - I THINK. Also - for a fujitsu lifebook laptop with centrino processor should i need/use the 686 kernel or is the 386 kernel adequate? and why?

I did download the latest i915 drivers for the intel855gm from that site, and the common files - but they dont seem to take when i follow the instructions. I really appreciate any advice here. Thanks

---

### Post by sherpah on 2006-08-08
bump - cause im losing my mind over this seemingly unsolveable problem

---

### Post by darrenm on 2006-08-09
Tried mailing intel?

---

