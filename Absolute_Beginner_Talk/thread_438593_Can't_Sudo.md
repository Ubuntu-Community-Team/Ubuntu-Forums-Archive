---
title: "Can't Sudo ?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by sdgreen on 2007-05-09
Weird problem. Installed 7.04, all went well with three problems.

1. Can not use su, sudo in any of the terminals. 
2. I have a Nvidia 6600GT, but xorg identifies as a FX5200, wrong driver ! But cannot edit xorg.conf.
3. GDM has sound, KDM does not.

How to fix?

---

### Post by alienexplorers on 2007-05-09
did you try gksudo. Your sudoers file may be corrupt.

---

### Post by taurus on 2007-05-09
1.  What happens when you use sudo?  Does it except your password, the same password that you login with?  Otherwise, what's the output of this command from a terminal?

```
id
```

2.  What's the output of this command from a terminal again?

```
lspci
```

---

### Post by psusi on 2007-05-09
Insufficient data for meaningful answer.

"I can't sudo" is about as descriptive as "my computer is broke".  You will have to be more specific to get help.  How did you try to use it, and what happened instead of what was supposed to?

---

### Post by sdgreen on 2007-05-09
output of su
sdgreen@sdgreen-garage:~$ su
Password:
su: Authentication failure
Sorry.
sdgreen@sdgreen-garage:~$

gksu works however.

thanks

---

### Post by sdgreen on 2007-05-09
more data...

sdgreen@sdgreen-garage:~$ id
uid=1000(sdgreen) gid=1000(sdgreen) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(sdgreen)
sdgreen@sdgreen-garage:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 01)
sdgreen@sdgreen-garage:~$

---

### Post by sdgreen on 2007-05-09
xorg.conf

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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
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
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "IBM G78"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "IBM G78"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "960x529" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "960x529" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "960x529" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "960x529" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "960x529" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "960x529" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by drowner on 2007-05-09
this seems a stupid question.... are you typing your password correctly?

---

### Post by sdgreen on 2007-05-09
Yes .. same one to sign one or do updates

---

### Post by alienexplorers on 2007-05-09
Are you sure you don't have CAPS LOCK on by mistake.  I have done this before and felt reqally dopey when I discovered what was wrong.

---

### Post by bobplano on 2007-05-09
the command su by itself doensn't work in ubuntu. i don't know why but you need to do 
```
sudo su
```
if *sudo* doesn't work, that is a different problem from su

---

### Post by sdgreen on 2007-05-09
no caps....

Must be something corrupt but have no idea what, or where to look. Either that or, something is strange with my authentication system.

---

### Post by drowner on 2007-05-10
> **sdgreen said:**
> no caps....

Must be something corrupt but have no idea what, or where to look. Either that or, something is strange with my authentication system.

So you can't su

Can you sudo?

What happens if you try and sudo?

---

### Post by rich.bradshaw on 2007-05-10
lol

There is no root account in Ubuntu, hence su won't work.

Instead prefix commands by sudo, if you want to run only a few i.e.

sudo apt-get update

or type

sudo -i

to get into interactive mode.

---

### Post by psusi on 2007-05-10
> **rich.bradshaw said:**
> lol

There is no root account in Ubuntu, hence su won't work.



This is not true.  There is ALWAYS a root account.  By default, Ubuntu does not set a password on the root account, and with no password, su won't let you switch to root, gdm won't let you log in, and so on.  You can still login as root on a tty.  

sudo is the preferred privilege escalation method in Ubuntu.  It is much more configurable and granular than su.

---

### Post by kragen on 2007-05-10
About your nvidia question:

To my knowledge, all nvidia cards use the same driver, unless you are having graphical problems, (in which case I could be wrong), the fact your card is incorrectly identified shouldn't actually affect anything.

-- EDIT --

About your su question, the command

```
su
```

Will fail, because Ubuntu doesn't provide the root account with a password. If you want to execute a command as root, then you need to prefix it with sudo, for example:

```
sudo gedit /etc/X11/xorg.conf
```

Then you enter your password and everything should be dandy.

If you want to "be" root, then you need to use

```
sudo su
```

Instead. 
If you really really want to be root, you can assign your root account a password (search for it on google), but it's not recommended, and there is no real need to either. sudo is far more secure, there is no real need to activate the root account.

---

