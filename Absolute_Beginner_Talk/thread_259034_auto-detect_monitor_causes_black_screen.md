---
title: "auto-detect monitor causes black screen"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-09-16
while running dpkg-reconfigure xserver-xorg, i get to the part where it auto-detects monitor then it goes black and never goes anywhere. during a regular boot, it goes black after the ubuntu screen shows the progress bar completed.

any help is greatly appreciated!

---

### Post by shanepardue on 2006-09-16
please help!

---

### Post by bodhi.zazen on 2006-09-16
Deatils?

Videocard ?

Monitor ?

Laptop ?

Does it lock up or return you to a CLI ?

---

### Post by shanepardue on 2006-09-16
nvidia geforce 4 420 go
toshiba 6100

it locks up when using the nvidia driver, but not with the nv

i have to hard power off.

---

### Post by bodhi.zazen on 2006-09-16
Try this page. It is old and is for Debian, but it may help. There are instructions on how to configre X ("Configuration of XFree86").

[Debian toshiba 6100](http://www.risc.uni-linz.ac.at/people/gbodnar/www/toshiba/)

---

### Post by shanepardue on 2006-09-17
oh awesome! thanks for the link! i have a question...by enabling the twinview, does that mean i have to have dual-monitors or is that just enabling if i want to use the video-out? here's what they're recommending as the config..THANK YOU!!

```
Section "Device"
        Identifier      "NVIDIA GeForce 4 420 Go TwinView"
        Driver          "nvidia"
        BoardName       "Unknown"
        VideoRam        32768
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "true"
        Option          "TwinView"
        Option          "SecondMonitorHorizSync" "31.5-100"
        Option          "SecondMonitorVertRefresh" "55-100"
        Option          "TwinViewOrientation" "Clone"
        Option          "MetaModes"  "1024x768, 1024x768; 1024x768, NULL"
        Option          "ConnectedMonitor" "DFP,CRT"
EndSection

For the monitor the corresponding section is

Section "Monitor"
        Identifier      "Toshiba 6100TFT"
        VendorName      "Toshiba"
        ModelName       "Unknown"
        HorizSync       31.5-100
        VertRefresh     55-100
        Option          "dcc" "false"
EndSection

Then to have both the LCD and the external video port working, you can define the screen with the following section

Section "Screen"
        Identifier      "Twin Screen"
        Device          "NVIDIA GeForce 4 420 Go TwinView"
        Monitor         "Toshiba 6100TFT"
        DefaultDepth    24
        SubSection "Display"
                Depth   24      
                Modes   "1024x768"
        EndSubSection
        Option "IgnoreEDID" "true,true"
EndSection

Finally, the server is configured by the section

Section "ServerLayout"
        Identifier      "Twin Layout"
        Screen          "Twin Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Generic Mouse"
EndSection

```

---

### Post by bodhi.zazen on 2006-09-17
It looks like this configuration does not require dual monitors. Specifically it appears with this set-up the monitors are mirrored....

Try and see what happens, not much to loose....

---

### Post by bodhi.zazen on 2006-09-17
You do understand this is not a complete xorg.conf ?

You will need to cut and paste these sections into your current xorg.conf.

I advise you copy your current corg.conf onto a ? usb or floppy, cut and paste on the OS you are posting to ubuntu.

If you need help, post your original, un-edited xorg.conf...

---

### Post by shanepardue on 2006-09-18
yeah, i'm aware it's not the whole config file and i pasted the sections into my config file. It caused xserver to not load. i have since pasted back my old config with "nv".

i would include the entire log file, but i'm not sure if it would help. thanks again for your help. i'll try googling some more. if you got any ideas, let me know!

---

### Post by bodhi.zazen on 2006-09-18
post log file.

---

### Post by shanepardue on 2006-09-18
i'm not sure how often it logs errors, but i hope this is the right one. thank you for your patience!

---

### Post by bodhi.zazen on 2006-09-18
I do not know if it will help, comment out (add a # at the beginnig) your glx module in the Module" section;

#  Load "glx"

My only other thought is did you install the nvidia driver for the legacy cards?

---

### Post by shanepardue on 2006-09-18
i'll try commenting that out this evening (when i'm able to). as far as the driver, i used the automatix one which i believe is the correct one for my video card. am i right?

---

### Post by bodhi.zazen on 2006-09-18
See these threads:

[GeForce 4 420](http://ubuntuforums.org/showthread.php?t=209157#4)

[GeForec - Free BSD](http://lists.freebsd.org/pipermail/freebsd-questions/2006-April/118484.html)

Look at the first thread, edit (vi os-registry.c).

You can use gedit on nano rather then vi.

```
nano os-registry.c
```And edit as instructed.

Then re-install nvidia driver.

[color=blue]Cool Avatar[/color]

---

### Post by shanepardue on 2006-09-18
oh man! thanks for helping me! i'm sure this will all work judging by the results everyone is getting. i'm getting stuck where i'm supposed to extract the video driver, but it seems the drivers aren't archived files anymore. now i'm supposed to run the file as "sh <filename>". i did it (outside of x) and this is what the logfile had to say.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Sep 18 22:19:09 2006

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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (temporary DNS error (try again
       later))
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by bodhi.zazen on 2006-09-18
Install the linux headeeres and re-try:

```
sudo aptitude install nvidia-glx linux-headers-`uname -r`
```

then remove the hash in front of the glx option I had you disable earlier (# load "glx").

You may also need build-essential:```
sudo aptitude install build-essential
```

---

### Post by shanepardue on 2006-09-19
i'm sorry i'm asking so many questiosn, but i managed to get the driver installed through that program, but now i can't find where to edit that file. i've tried "sudo find / -name <filename>" and it doesn't find it.

thanks again for your help!!

---

### Post by bodhi.zazen on 2006-09-19
Try this:

```
sudo nano /etc/modprobe.d/options
```

At the end of the file add this:> options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1

ctrl-X to exit nano, type "Y" to save changes.

now edit xorg.conf:```
nano /etc/X11xorg.cong
```

Add the followindg lines to "screen" section"
> Section "Screen"
        Identifier      "Twin Screen"
        Device          "NVIDIA GeForce 4 420 Go TwinView"
        Monitor         "Toshiba 6100TFT"
        DefaultDepth    24
        [b]Option "ExactModeTimingsDVI" "TRUE"
        Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"[/b]
        SubSection "Display"
                Depth   24      
                Modes   "1024x768"
        EndSubSection
        Option "IgnoreEDID" "true,true"
EndSection

Again save file :Ctrl-X to exit, type "Y" to save.

Re-start x....

---

### Post by shanepardue on 2006-09-19
i added the bold part to the screen section. wasn't sure if you meant subsitute my whole screen section with that or just add the bold lines. after adding just the bold lines, X failed saying, "no screens found" in the error output. was i supposed to substitute the whole screen section?

---

### Post by bodhi.zazen on 2006-09-19
Just the bold lines.

attach a copy of xorg.conf.

---

### Post by shanepardue on 2006-09-19
here she is.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
    Option         "XkbDisable" "true"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
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
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option "ExactModeTimingsDVI" "TRUE"
    Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

```

---

### Post by bodhi.zazen on 2006-09-19
Your xorg.conf seems incomplete,  particularly the > Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Driver         "nvidia"
EndSection

Lets start anew...

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.not_quite
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig
sudo nano /etc/X11/xorg.conf
```

Add the two lines as above, exit nano and save your edit.

Re-start X....

---

### Post by shanepardue on 2006-09-19
whenever i type your command for reconfiguring the xorg config i get "postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf_(a bunch of numbers thereafter)".

whenever i try just dpkg-reconfigure xserver-xorg, i get that error message right after i choose the desired color bit.

maybe that's why i can't get a complete xorg.conf.

---

### Post by bodhi.zazen on 2006-09-19
This is a nomral message. You box is telling you you overwrote a file and that it made a backup if needed. You can ignore it.

If this does not work, re-post your new xorg.conf......

---

### Post by shanepardue on 2006-09-19
i followed the steps you provided, but it just breaks the xserver. unfortunately, i ran out of battery on the machine and realized i had left it at one of my jobs so i couldn't post the xorg.conf tonight. i'm pretty upset i left it. oh well, i guess i can paste the file tomorrow night.

---

### Post by bodhi.zazen on 2006-09-19
LOL :lol: You have to laugh or you will go insane....

sorry that did not work.

Edit xorg.conf, remove the two previous lines and try:```
Option "ExactModeTimingsDVI"
Option "UseEdidDpi" "FALSE"
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
```

---

### Post by shanepardue on 2006-09-20
still not working. and yes, my xorg does look incomplete even after the steps you provided. here's how it looks now.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
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
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
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
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    8
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
    Option "ExactModeTimingsDVI"
    Option "UseEdidDpi" "FALSE"
    Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
EndSection
```

---

### Post by bodhi.zazen on 2006-09-20
Back up this file so you can restore it if needed.

Use this from your original post:
> Section "Device"
        Identifier      "NVIDIA GeForce 4 420 Go TwinView"
        Driver          "nvidia"
        BoardName       "Unknown"
        VideoRam        32768
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "true"
        Option          "TwinView"
        Option          "SecondMonitorHorizSync" "31.5-100"
        Option          "SecondMonitorVertRefresh" "55-100"
        Option          "TwinViewOrientation" "Clone"
        Option          "MetaModes"  "1024x768, 1024x768; 1024x768, NULL"
        Option          "ConnectedMonitor" "DFP,CRT"
EndSection

And try with the current 3 option lines in "screen", then the first 2 option lines, then no lines...

I then have only 1 more trick:

replace the previous options line in modprobe.d/options:
 
```
sudo nano /etc/modprobe.d/options
```

Use just this option at the end of the file (delete previous):
```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=4
```

---

### Post by shanepardue on 2006-09-20
i did everything you said and i'm sad to say that it's still not working. i really appreciate all your help, but i understand if you're out of ideas.

---

### Post by bodhi.zazen on 2006-09-20
Ouch, sorry...

---

