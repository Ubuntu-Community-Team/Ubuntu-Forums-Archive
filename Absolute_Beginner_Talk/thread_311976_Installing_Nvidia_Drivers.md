---
title: "Installing Nvidia Drivers"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by ChiaroScuro on 2006-12-03
I am having much trouble installing the required drivers from NVIDIA.
I have been following this guide: URL="http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/nVIDIA"]http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/nVIDIA[/URL]
I Dont even know what driver i need to install. I have tried a couple to no avail. 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Dec  1 22:52:47 2006

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA RIVA TNT2/TNT2 Pro GPU installed in this system is
         supported through the NVIDIA legacy Linux graphics drivers.  Please
         visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information. 
         The 1.0-9742 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 1.0-9742
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         [www.nvidia.com](www.nvidia.com).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.17-10-generic/build'
-> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
ERROR: Unable to determine the NVIDIA kernel module filename.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

What driver do i need?
Why wont cant sh open NVIDIA-Linux-x86-1.0-7184--pkg1.run?

Any help would be greatly appreciated!!!

---

### Post by taurus on 2006-12-03
[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by Sprite1990 on 2006-12-03
> **taurus said:**
> [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

Worked for me :p

---

### Post by xpod on 2006-12-03
Mabey a wee look at Automatix2 would`nt go amiss..

You`ll find easy install of your drivers and another couple of dozen useful app`s and utilities in it..

Theres all the time in the world to learn the "proper" ways as some would have you do but AX is a beginners saviour in a whole lot of cases and a must for those starting out i reckon...

Theres even one click install now as far as i know

EDIT.....[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by ChiaroScuro on 2006-12-03
when to url and followed steps but, sudo nvidia-xconfig --no-composite renered nothing...
also:   glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by taurus on 2006-12-03
Paste your /etc/X11/xorg.conf here then!

```
cat /etc/X11/xorg.conf
```

---

### Post by ChiaroScuro on 2006-12-03
cat /etc/X11/xorg.conf
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

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "NVIDIA Corporation NV5 [RIVA TNT2/TNT2 Pro]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "MultiSync 77"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV5 [RIVA TNT2/TNT2 Pro]"
        Monitor         "MultiSync 77"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by PurplePenguin on 2006-12-03
I second Automatix 2.  You don't need to know a thing about which driver you need - it'll do everything for you. :)

---

### Post by ChiaroScuro on 2006-12-03
Yeah, but this is my 4th day using linux, if i just have everything done for me I just won't learn, ya know?

---

### Post by taurus on 2006-12-03
If you look at your /etc/X11/xorg.conf, you are still using nv driver instead of nvidia!!!

```

Section "Device"
Identifier "NVIDIA Corporation NV5 [RIVA TNT2/TNT2 Pro]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection

```
So, edit it and change the "nv" to "nvidia" and restart X with <Ctrl><Alt>Backspace...

---

### Post by Mimsy on 2006-12-03
> **ChiaroScuro said:**
> Yeah, but this is my 4th day using linux, if i just have everything done for me I just won't learn, ya know?

Very true. Automatix is for people like me, who had this one evening to get things set up and running, and who *had* to be able to use the laptop the following day. In that situation, Automatix is a life-saver. :) 

/Mimsy

---

### Post by ChiaroScuro on 2006-12-04
Taurus, I got it bud!!! I was extremely happy to see the Nvidia Logo on Restart. Thanks for sharing that COFFEE!:D

---

### Post by taurus on 2006-12-04
> **ChiaroScuro said:**
> Taurus, I got it bud!!! I was extremely happy to see the Nvidia Logo on Restart. Thanks for sharing that COFFEE!:D
So you are running nvidia driver for your graphic card now, eh!

Have fun.

---

### Post by PurplePenguin on 2006-12-04
> Yeah, but this is my 4th day using linux, if i just have everything done for me I just won't learn, ya know?

Very true. :)  Maybe I'm too cautious, I just always worry about people getting too frustrated with it and going back to their old OSes!  :D

---

### Post by ChiaroScuro on 2006-12-05
Man, I completed installation of the driver, which led me in the direction to install beryl right? No problems with installation, but it seems to be that i have a GPU that was left behind. I get no windows borders with beryl, so i research it and find that the culprit might just be my handy NV5 RIVA TNT2/TNT2 PRO. Is there any hope for me?

---

### Post by xpod on 2006-12-05
> Yeah, but this is my 4th day using linux, if i just have everything done for me I just won't learn, ya know?

Unless you got plans on going somewhere else you got all the time in the world to learn the many ways of doing stuff.:D 

Im not to sure about specifics but i sometimes had issues with windows borders and just changing the windows manager from beryl to metacity and back again after a "ctrl-alt-backspace" usually sorts it out.Not had it happen for a while now though:-k 

Ps...you dont want everything done FOR you now do you;) 
Good luck m8

---

### Post by LaneLester on 2006-12-06
There seems to be something wrong with the nvidia-glx file. Automatix quit during the install with this: 1 - An apt-based error occured and installation was unsuccessful

When I tried earlier to install that file with Synaptic, I got this:
E: /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb: subprocess pre-installation script returned error exit status 2

I deleted the archive file before I ran Automatix, and it downloaded a fresh copy.

Lane

---

### Post by PILGU on 2006-12-06
try

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

After that download and installation is completed, run

sudo dpkg-reconfigure xserver-xorg

make sure to chose nvidia in place of nv during the wizard.

it has worked for me.

---

### Post by LaneLester on 2006-12-06
Thanks for all the suggestions! Alberto Milone's envy installer did the trick for me.

Lane

---

