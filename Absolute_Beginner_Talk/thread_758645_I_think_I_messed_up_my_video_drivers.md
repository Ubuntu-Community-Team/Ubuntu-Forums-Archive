---
title: "I think I messed up my video drivers"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Paraphysicist on 2008-04-18
...permanently.  I was trying to get a game to work and the tech support said to make sure you have the latest Nvidia drivers.  I went to [http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-03.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-03.html) and followed the instructions.  I had to disable x and press ctrl+alt+f1.  Then running as root, I typed this command: NVIDIA-Linux-x86-169.12-pkg1.run  

A box popped up and said something abou met not having the right kernel and asked me if Nvidia would search for one.  I agreed.  Another box came up (this is all dos-style, not a gui) and asked if I would like Nvidia to build a kernel or something to that effect.  I agreed and it a green bar started filling up.  After it was finished, immediately a message came up saying that I was in limited graphics mode.  

I haven't been able to get out of this limitd graphics mode, it's exactly like safe mode in windows.  I tried to go back to the proprietary 8 series drivers I had before in the Restricted Driver Management, and I enabled it, but I'm still in low graphics mode. 

Also I get this after running compiz in the terminal:

slippy@slippy-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x100002a (awn_elemen)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.



Is there any way to fix this?  Also is there a way I can go back to a few hours ago, something similar to system restore?  Any help or advice is greatly appreciated.  Thanks

---

### Post by bumanie on 2008-04-18
What model of nvidia card do you have? There is no system restore equivalent as part of the OS, although recently some third party people have started trying to make something similar for ubuntu. Not sure how successful they've been as yet. At least you can boot in safe mode, it should be fixable as you have access to ubuntu.

---

### Post by Paraphysicist on 2008-04-18
Darn, I was hoping there was some kind of restore option.  If they do make one, that would be awesome.  The card is an 8600gt.  Hopefully it is fixable, I'll keep trying stuff.

---

### Post by herbster on 2008-04-18
This should be easy, first you should realize that you installed the same driver that the restricted driver is. All you did is grab the package from nvidia's site.

Paste the contents of this file:

```
gedit /etc/X11/xorg.conf
```

---

### Post by OffAxis on 2008-04-18
did it register the package correctly with dpkg?

```
dpkg -l nv*
```

here's my dpkg list for a normal install (with restricted driver) for an nvidia card

```
me@mine:/var/log$ dpkg -l nv*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  nvidia-glx     <none>         (no description available)
un  nvidia-glx-leg <none>         (no description available)
ii  nvidia-glx-new 100.14.19+2.6. NVIDIA binary XFree86 4.x/X.Org 'new' driver
un  nvidia-glx-src <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
ii  nvidia-kernel- 20051028+1ubun NVIDIA binary kernel module common files
un  nvidia-new-ker <none>         (no description available)
un  nvidia-setting <none>         (no description available)

```
you should be able to do a 
```
sudo apt-get remove <package name>
```
or
```
sudo apt-get purge <package name>
```

to clear out the offending package and then re-install the regular nvidia ones from the repos.

you may have to run through
```
sudo dpkg-reconfigure xserver-xorg
```
to reset to the regular driver.

---

### Post by Paraphysicist on 2008-04-18
Herbster and Offaxis, thank you for the replies

> **herbster said:**
> This should be easy, first you should realize that you installed the same driver that the restricted driver is. All you did is grab the package from nvidia's site.

Paste the contents of this file:

```
gedit /etc/X11/xorg.conf
```

I ran the command but I got this output:

slippy@slippy-desktop:~$ sudo su
[sudo] password for slippy:
root@slippy-desktop:/home/slippy# gedit /etc/X11/xorg.conf

(gedit:6943): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I saved the file anyway and disabled then reenabled the restricted Nvidia driver, but no change.

---

### Post by Paraphysicist on 2008-04-18
THis is what I get when I run dpkg:

slippy@slippy-desktop:~$ dpkg -l nv*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  nvidia-glx     <none>         (no description available)
un  nvidia-glx-leg <none>         (no description available)
ii  nvidia-glx-new 100.14.19+2.6. NVIDIA binary XFree86 4.x/X.Org 'new' driver
un  nvidia-glx-src <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
un  nvidia-kernel- <none>         (no description available)
ii  nvidia-kernel- 20051028+1ubun NVIDIA binary kernel module common files
un  nvidia-new-ker <none>         (no description available)
un  nvidia-setting <none>         (no description available)



I tried to remove the package using both commands, but it said the package couldn't be found:


slippy@slippy-desktop:~$ sudo apt-get remove NVIDIA-Linux-x86-169.12-pkg1.run
[sudo] password for slippy:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package NVIDIA-Linux-x86-169.12-pkg1.run

slippy@slippy-desktop:~$ cd /home/slippy/Nvidia
slippy@slippy-desktop:~/Nvidia$ sudo apt-get remove NVIDIA-Linux-x86-169.12-pkg1.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package NVIDIA-Linux-x86-169.12-pkg1.run

slippy@slippy-desktop:~/Nvidia$ cd
slippy@slippy-desktop:~$ sudo apt-get purge NVIDIA-Linux-x86-169.12-pkg1.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package NVIDIA-Linux-x86-169.12-pkg1.run

slippy@slippy-desktop:~$ cd /home/slippy/Nvidia
slippy@slippy-desktop:~/Nvidia$ sudo apt-get purge NVIDIA-Linux-x86-169.12-pkg1.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package NVIDIA-Linux-x86-169.12-pkg1.run


Is it possible that I'm putting the wrong package name in?

---

### Post by herbster on 2008-04-18
Yeah, my bad I suggested gedit which needs X, but it does look like you just need to get rid of the nvidia driver completely, reinstall it and then config your xorg. This should do it:

```
sudo apt-get --purge remove nvidia*
```

Then

```
sudo apt-get install nvidia-glx-new
```

Reboot, then paste the contents of your xorg.conf like this:

```
cat /etc/X11/xorg.conf
```

---

### Post by Neo0351 on 2008-04-18
try installing the driver with envy.  if you dont want to you will need to disable the nv driver
```
sudo gedit /etc/default/linux-restricted-modules-common
```
last line should look like this
```
DISABLED_MODULES="nv"
```

---

### Post by Paraphysicist on 2008-04-18
Herbster, I did what you said and now i don't get the low graphics mode message.


Here are the xorg contents:

slippy@slippy-desktop:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "NVIDIA GeForce 8 Series"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
        Vendorname      "NVIDIA"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 640     480
                Modes           "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

---

### Post by Paraphysicist on 2008-04-18
I tried to configure xorg, and I got the monitor resolution right, but my sound, avant window navigator, and compiz don't work.  Is there a way to get them back?

---

### Post by herbster on 2008-04-20
When you turn on Desktop Effects nothing happens?

Your sound is another issue. Check your mixer levels in the volume settings, be sure all is unmuted and raised up. Paste the output of this:

```
lspci
```

And run this, paste the output and tell me if you hear the voice or not:

```
speaker-test -c2 -twav -Ddefault
```

Hit CTRL+C to end that test.

---

### Post by Paraphysicist on 2008-04-21
Herbster,

 thanks for the replies.  When I try to enable the advanced effects, I get a message saying they cannot be enabled.  The speaker icon on the top right of the screen has a red circle slash through it.   Also, Avant window navigatorwon't run and I can't keep any windows (they don't tab at the bottom; they're still open, just buried for good).   I'm probably going to reinstall, but it'd be interesting to know what the code of the Nvidia driver did to the computer.

Here is the output of lspci:

slippy@slippy-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by Paraphysicist on 2008-04-21
I tried to post theout put of the sound test, but I keep getting this message: 

1.  You have included 48 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

:confused:

---

### Post by Frasc0 on 2008-05-05
Got exactly the same problems as installing my GeForce 7300. Now no sound and still can't enable effects. No window problem for me. :(

---

