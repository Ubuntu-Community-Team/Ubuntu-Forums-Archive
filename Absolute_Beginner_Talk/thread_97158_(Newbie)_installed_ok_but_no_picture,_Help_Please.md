---
title: "(Newbie) installed ok but no picture, Help Please"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by theflyingbeard on 2005-11-30
Hi, I have quite a bit of experiance with computers and microshaft, but I'm new to Linux. 

I downloaded the Ubuntu ISO burned the CD and ran the install with no real problem at all. Everything worked well untill the final screen. I'm guessing that is the gui login screen, but I cant actually see it. The screen is blank. 

Pressing return gets a nice little clicking sound, and typing in my user name then tab and my password gets me a lovely chorus of harmonious tones and chirps from the sound system but still no picture.

After several hours on this forum I have discovered Alt+Ctrl+Backspace which shutsdown X Server and allows me to see text and a command line.

More searching leads me to believe that it may be my graphics card is related to the problem. It being a Nvidia card (FX5600XT).

Having shutdown X Server I am faced with a screen full of text just before the "waiting for X server to shutdown" and then the command prompt.

The text goes like this:
---------------------
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No Symbols Found
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No Symbols Found
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No Symbols Found
skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No Symbols Found

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:   Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

then a list of font renderer warnings

--------------------

I have also discovered startx which seems to take me back into the gui with the lovely chorus again but no picture.

I have also tried some code that was suggested on one of the threads to install nvidia drivers using 
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

But I have no idea what any of that means or does, there was some kind of error after the last one, but the next instruction stumped me anyway. it said to insert the following lines into the new file, but I have no new file, I dont know of any linuxt text editors or even how to change directory or acces any log files.

I Gave up and reinstalled after that.

So here I am with a fresh installation which seems to be working but I have no picture. What should I do now? Anybody please.......

---

### Post by Estariel on 2005-11-30
please post the Device section of your /etc/X11/xorg.conf file.

Just kill the X server and type
```
less /etc/X11/xorg.conf
```

scroll down till you find something similar to this:

```
Section "Device"
  BoardName    "GeForce Go 6200 (0x0167)"
  BusID        "1:0:0"
  Driver       "nvidia"
  Identifier   "Device[0]"
  Option       "XaaNoOffScreenPixmaps" "on"
  Option       "XaaNoPixmapCache" "on"
  #Option       "NvAGP" "2"
  #Option       "NvAGP" "0"
  #Option       "NvAGP" "3"
  #Option       "NvAGP" "1"
  Screen       0
  VendorName   "NVidia"
EndSection

```

Post yours please.

---

### Post by nab on 2005-11-30
Hi,

take a look here:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=HOWTO%3A+Latest+NVIDIA+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=HOWTO%3A+Latest+NVIDIA+drivers)

This should help :) 

Niko

---

### Post by theflyingbeard on 2005-11-30
[QUOTE=Estariel]please post the Device section of your /etc/X11/xorg.conf file.

Just kill the X server and type
```
less /etc/X11/xorg.conf
```

scroll down till you find something similar to this:

```
Section "Device"
  BoardName    "GeForce Go 6200 (0x0167)"
  BusID        "1:0:0"
  Driver       "nvidia"
  Identifier   "Device[0]"
  Option       "XaaNoOffScreenPixmaps" "on"
  Option       "XaaNoPixmapCache" "on"
  #Option       "NvAGP" "2"
  #Option       "NvAGP" "0"
  #Option       "NvAGP" "3"
  #Option       "NvAGP" "1"
  Screen       0
  VendorName   "NVidia"
EndSection

```

Post yours please.[/QUOTE]

Thanks for a quick reply,

Section "Device"
           Identifier    "NVIDIA Corporation NV31 [GeForce FX 5600XT]"
           Driver        "nv"
           BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
           Identifier    "Generic Monitor"
           Option       "DPMS"
EndSection

I if you need more from the conf file let me know, but I have to type it manually.

---

### Post by theflyingbeard on 2005-11-30
[QUOTE=nab]Hi,

take a look here:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=HOWTO%3A+Latest+NVIDIA+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=HOWTO%3A+Latest+NVIDIA+drivers)

This should help :) 

Niko[/QUOTE]

Thanks Niko but I already looked at that and dismissed it as I dont have access to the gui and cant use the mouse.

---

### Post by Estariel on 2005-11-30
[QUOTE=theflyingbeard]Thanks for a quick reply,

Section "Device"
           Identifier    "NVIDIA Corporation NV31 [GeForce FX 5600XT]"
           Driver        "nv"
           BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
           Identifier    "Generic Monitor"
           Option       "DPMS"
EndSection

I if you need more from the conf file let me know, but I have to type it manually.[/QUOTE]

ok, that looks normal, but maybe the "nv" driver does not support your graphics card.
Thus, get nvidias driver as you did before:
```

sudo apt-get install nvidia-glx
 sudo apt-get install nvidia-settings

```

then change the
```

           Driver        "nv"

```
line in your config file to
```

           Driver        "nvidia"

```

to edit the file, do the following
```

sudo nano /etc/X11/xorg.conf

```
change the line.
save the file (I think it is ctrl+o)
exit the text editor (ctrl+q)

try starting the x server (startx)

tell me if it worked :) (but I'm out for lunch now for an hour or so)

---

### Post by theflyingbeard on 2005-11-30
Thanks Estariel but no joy.

The screen flashed and rolled a bit when I started the X Server, then I got the intro sound but still no picture.

On exiting X Server again I did get the following messages:
skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.0": No symbols found
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdr.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdr.a is unresolved!
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning etc. etc. same as before.

---

### Post by teaker1s on 2005-11-30
if you can't see screen hit esc at boot choose recovery in grub
sudo dpkg-reconfigure xserver-xorg
you will need to work out graphics card memory mb x 1024 and also you will need to find the horizontal sync and vertical refresh rate of your monitor for this proceedure
note nv driver more likely to work but has no open gl 
nvidia driver open gl but needs more setup to boot successfully

I recomend nv as your first try

---

### Post by Estariel on 2005-11-30
Hmn.
For every monitor, there exists something calles a horizontal sync rate and a vertical refresh rate (like teaker1s said).

We need to know both of these for the next step.

The easiest way would be if you could look them up in your monitor manual (Most of the time they are called HorizSync and VertRefresh)

It should be something like this: (This is my monitor)
  HorizSync    30-82
  VertRefresh  58-75

If you don't have the manual, google for your exact monitor model.
If you cannot find it, post the model number, and I'll try to help.

Once you have done that, find the   HorizSync  and VertRefresh lines in your /etc/X11/xorg.conf file and adjust them.

Also, I don't think that the nv driver is easier to set up than the nvidia driver. nvidias driver most of the time just works (at least for all the computers I have set up)

---

### Post by theflyingbeard on 2005-11-30
YEEEEEEHA! I'm up and running!!

Thank you very much for your help Estariel and teaker1s.
Thanks to Estariel I have the Nvidia drivers installed and learned some command line methods to access read and edit relavent files. and Thanks to teaker1s I'm now aware of the recovery mode and the ability to step through the xserver reconfiguration.

After seeing teaker1s post, 
I took a gamble and dived into the reconfiguration with the nvidia drivers installed ignoring the recomendation to try the nv driver first. I figured that I'd give it ago and reinstall from scratch if I screwed up, then re-read this post and get back to where I was. 

After entering sudo dpkg-reconfigure xserver-xorg 
I found I was asked loads of questions, more than I anticipated, but I think that it already had most of the correct information. I did have to enter the memory size, but I didnt have to enter the H & V sync rate. 

I was given a choice of Simple Medium or Advanced just prior to setting the display mode (I think). anyway I chose Medium and was presented with a selection of modes I was familiar with, I selected 1024x768@60Hz and I think that was the key. So I OKed loads more and accepted the defaults AND HERE WE ARE :)

So thanks to both of you. I am very grateful and Impressed at the speed with which this thread was responded to.

Many Thanks
Adrian

---

### Post by Estariel on 2005-11-30
great that it worked out :)

Have fun with your new system!

---

