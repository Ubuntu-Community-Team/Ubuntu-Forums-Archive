---
title: "Scree Resolution"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-15
Well my regular screen resolution is 1280 by 1024 and I shut my pc down and whent to a friends house booted it up and it is stuck at 680 by 400 does anybody know how I would fix this.

---

### Post by rbprogrammer on 2007-06-15
i may not be able to help, but the people who can help definitely need some more information.. like the type of computer, video card, etc..

also, did you install any programs after you first started up and before you shut down the time before the resolution changed?

---

### Post by jonward0690 on 2007-06-15
Well I messed with my scree saver and I do not have a fancy graphics card it is a plane jane card from dell hold on while I find out what it is.

---

### Post by w4ett on 2007-06-15
Why don't you post the output of: lspci    and also your    xorg.conf     and let us have a look see.  :)

---

### Post by jonward0690 on 2007-06-15
Were can I find this info it is hard to see with this low of a resolution.

---

### Post by bobplano on 2007-06-15
you can run the commands in the terminal which is in applications>accessories>terminal. 
```
lspci
cat /etc/X11/xorg.conf
```
then just copy and paste to here. be sure you use a capital X in the second command or it will just be a blank file

---

### Post by w4ett on 2007-06-15
Applications>Accessories>Terminal and type in: lspci  copy and past the results

Next type in:   sudo gedit /etc/X11/xorg.conf   copy and paste the results

---

### Post by jonward0690 on 2007-06-15
Here is the lspci               jon@jon-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem
jon@jon-desktop:~$

---

### Post by jonward0690 on 2007-06-15
Here is the xorg conf                                           jon@jon-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem
jon@jon-desktop:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
  identifier "Intel Corporation 82G965 Integrated Graphics Controller"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
EndSection

Section "Monitor"
  identifier "DELL 1907FP"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation 82G965 Integrated Graphics Controller"
  Monitor "DELL 1907FP"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" #
  identifier "device1"
  boardname "i810"
  busid "PCI:0:2:0"
  driver "i810"
  screen 1
EndSection
Section "screen" #
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" #
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection
jon@jon-desktop:~$

---

### Post by jonward0690 on 2007-06-15
> **w4ett said:**
> Applications>Accessories>Terminal and type in: lspci  copy and past the results

Next type in:   sudo gedit /etc/X11/xorg.conf   copy and paste the results

Ok here it is               # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/usr/share/fonts/X11/cyrillic"
  FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath "/usr/share/fonts/X11/Type1"
  FontPath "/usr/share/fonts/X11/100dpi"
  FontPath "/usr/share/fonts/X11/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"

---

### Post by w4ett on 2007-06-15
Ok...seems your xorg.conf has been changed......in the terminal type:

sudo dpkg-reconfigure xserver-xorg

this will give you the graphical interface to reconfigure your xorg.conf resolution selections.

---

