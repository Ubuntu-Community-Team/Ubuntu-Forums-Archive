---
title: "NVIDIA Drivers for kira-dock"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by XtremeSki2001 on 2007-01-10
I'm interested in using some of the graphics programs used for some of the dock applications.

However, I need drivers for my graphics card. 

I check NVIDIA's website, but my graphics card wasn't listed.

Anyone know where to get drivers for a NVIDIA 6600GT to work with the dock bar applications (i.e. Beryl and Kira-Dock)?  I'm running Ubuntu 6.06

Thanks for any help in advance.

---

### Post by K.Mandla on 2007-01-11
Have you tried the nvidia-glx drivers from the repositories? It should include the 6600GT.

---

### Post by jondecker76 on 2007-01-11
Do a google for a script called envy. It does an excellent job of installing the drivers for you, it saved me a bunch of time and frustration

---

### Post by XtremeSki2001 on 2007-01-11
> **jondecker76 said:**
> Do a google for a script called envy. It does an excellent job of installing the drivers for you, it saved me a bunch of time and frustration

I tried using envy following [this guide]("http://albertomilone.com/nvidia_scripts1.html").

I get an error regarding "make" in my PATH, see log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Jan 11 09:21:21 2007

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
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
  X install prefix        : /usr/lib/xorg/modules
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.15-27-386
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
ERROR: Unable to find the development tool `make` in your path; please make
       sure that you have the package 'make' installed.  If make is installed
       on your system, then please check that `make` is in your PATH.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by XtremeSki2001 on 2007-01-11
> **K.Mandla said:**
> Have you tried the nvidia-glx drivers from the repositories? It should include the 6600GT.

I tried installing nvidia-glx from the[ following guide]("http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver").

and then restarted gnome desktop manager for changes to take effect via 

```
sudo /etc/init.d/gdm restart
```

How do I confirm that I'm all set Nvidia Driver wise?

---

### Post by XtremeSki2001 on 2007-01-11
> **XtremeSki2001 said:**
> I tried installing nvidia-glx from the[ following guide]("http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver").

and then restarted gnome desktop manager for changes to take effect via 

```
sudo /etc/init.d/gdm restart
```

How do I confirm that I'm all set Nvidia Driver wise?

Looks like it didn't work.  When I rebooted, itwouldn't allow me into the GUI interface.

I've reformatted now.

Now that the install is fresh, can someone point me to a place regarding the install of nvidia-glx or envy, which ever works best. 

Thanks a million!

---

### Post by XtremeSki2001 on 2007-01-11
> **K.Mandla said:**
> Have you tried the nvidia-glx drivers from the repositories? It should include the 6600GT.

OK, back to square one.

I installed the nvidia-glx package from synaptic.

Is this all I need to do?  It installed successfully.

---

### Post by docetes on 2007-01-11
auto matrix has a nvidia program which it'll install the nvidia drivers for you

---

### Post by Bachstelze on 2007-01-11
If the nvidia drivers installed correctly, you will have a nvidia logo appearing when your X starts. You can also check it with :

```
cat /var/log/Xorg.0.log | grep nvidia
```

It should output something similar to :

```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"

```

To install the nvidia drivers, see [here](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

---

### Post by XtremeSki2001 on 2007-01-11
> **HymnToLife said:**
> If the nvidia drivers installed correctly, you will have a nvidia logo appearing when your X starts. You can also check it with :

```
cat /var/log/Xorg.0.log | grep nvidia
```

It should output something similar to :

```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"

```

To install the nvidia drivers, see [here](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

Thanks!  I followed the guide verbatum and I get this at the very last step (I'm runnng Dapper):

```
erich@erich-desktop:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
erich@erich-desktop:~$

```

All the other steps worked fine, any ideas?

Running this:

```
cat /var/log/Xorg.0.log | grep nvidia
```

I don't get any thing back:

```
erich@erich-desktop:~$ cat /var/log/Xorg.0.log | grep nvidia
erich@erich-desktop:~$
```

---

### Post by Bachstelze on 2007-01-11
That means your X config file was not the default one - certainly due to the previous driver installation attempts - so it wasn't automatically modified, to prevent problems. do this :

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
gksudo gedit /etc/X11/xorg.conf
```

and paste the contents of the file, we'll tell you wat you need to modify.

---

### Post by XtremeSki2001 on 2007-01-11
> **HymnToLife said:**
> That means your X config file was not the default one - certainly due to the previous driver installation attempts - so it wasn't automatically modified, to prevent problems. do this :

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
gksudo gedit /etc/X11/xorg.conf
```

and paste the contents of the file, we'll tell you wat you need to modify.

Thanks for all the extra help Hymn ... can't wait to get this squared away and jump into the kiba-dock install :-D 

Contents of xorg.conf:

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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
```

---

### Post by XtremeSki2001 on 2007-01-12
Bump ... anyone know what Hymn planned to have me modify to the above file?

---

### Post by kpkeerthi on 2007-01-12
1. cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2. gksudo gedit /etc/X11/xorg.conf

Change 
> 
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection


to
> 
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
EndSection


and restart

See my signature for links to ubuntu documentation.

---

### Post by XtremeSki2001 on 2007-01-12
> **kpkeerthi said:**
> 1. cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2. gksudo gedit /etc/X11/xorg.conf

Change 


to


and restart

See my signature for links to ubuntu documentation.

Thanks ... they're all installed and ready to roll.  Thanks for the doc links too!

---

