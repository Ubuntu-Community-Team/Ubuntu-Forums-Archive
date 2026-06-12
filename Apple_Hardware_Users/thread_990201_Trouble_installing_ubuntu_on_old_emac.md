---
title: "Trouble installing ubuntu on old emac"
date: 2008-11-22
forum: Apple Hardware Users
---

### Post by Brii on 2008-11-22
i downloaded the powerpc version of ubuntu 8.10 and burned it on a dvd (because i dont have anymore blank cds) i burned it using poweriso (the version you pay for)

and it boots off the dvd and i get to the part where it shows the ubuntu logo and the loading bar the bar fills up then nothing it goes black and i cant type anything


i also downloaded the power pc version of 7.10 and it drops me into shell?????

---

### Post by stream303 on 2008-11-22
This should help out greatly, especially Oswaldkelso's xorg.conf file:

[http://ubuntuforums.org/showthread.php?t=695325](http://ubuntuforums.org/showthread.php?t=695325)

Having to manually configure your /etc/X11/xorg.conf file as root is pretty much mandatory for emacs.

---

### Post by Brii on 2008-11-22
> **stream303 said:**
> This should help out greatly, especially Oswaldkelso's xorg.conf file:

[http://ubuntuforums.org/showthread.php?t=695325](http://ubuntuforums.org/showthread.php?t=695325)

Having to manually configure your /etc/X11/xorg.conf file as root is pretty much mandatory for emacs.

so i have to type that all in

where

---

### Post by stream303 on 2008-11-22
Forgot to mention - stick to the ppc version, not Intel for that box. :)

If you can get to a virtual terminal, ie CTRL-ALT-F2 and login, you can use the nano editor:

```
sudo nano /etc/X11/xorg.conf
```

Type it all in, and then when done, (CTRL-O to write the file, CTRL-X to exit the nano editor)

reboot.

If it still doesn't come up, you might try going back into the commandline, and editing out the "files", "module", "input device", "server layout", and "dri" sections, and try again since Intrepid 8.10 may not like these kinds of manual section modifications.  The most important is to leave the driver, and the video frequencies in, as well as the resolution.

I don't own an emac, but see how far this goes.  You may have to hit the faqs for additional material, but this should get you started.

If you can't get to a virtual terminal via ctrl-alt-f2, you'll have to go deeper with a rescue-mode or linux-single mode and use the vi editor.  Hopefully you won't.

---

### Post by Brii on 2008-11-22
> **stream303 said:**
> Forgot to mention - stick to the ppc version, not Intel for that box. :)

If you can get to a virtual terminal, ie CTRL-ALT-F2 and login, you can use the nano editor:

```
sudo nano /etc/X11/xorg.conf
```

Type it all in, and then when done, (CTRL-O to write the file, CTRL-X to exit the nano editor)

reboot.

If it still doesn't come up, you might try going back into the commandline, and editing out the "files", "module", "input device", "server layout", and "dri" sections, and try again since Intrepid 8.10 may not like these kinds of manual section modifications.  The most important is to leave the driver, and the video frequencies in, as well as the resolution.

I don't own an emac, but see how far this goes.  You may have to hit the faqs for additional material, but this should get you started.

If you can't get to a virtual terminal via ctrl-alt-f2, you'll have to go deeper with a rescue-mode or linux-single mode and use the vi editor.  Hopefully you won't.

just to be sure i have to type this right:


Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/X11R6/lib/X11/fonts/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/X11R6/lib/X11/fonts/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/X11R6/lib/X11/fonts/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/X11R6/lib/X11/fonts/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/usr/X11R6/lib/X11/fonts/75dpi"
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
Load "vbe"
Load "dbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
Option "XkbOptions" "lv3:lwin_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 71-73
VertRefresh 70-140
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection


becuase i dont want to type that then figure out it was the wrong one =p

thanks for your help btw =]

---

### Post by stream303 on 2008-11-22
First thing to do is determine exactly what your model is, because the video cards differ:

[http://www.everymac.com/systems/apple/emac/index-emac.html](http://www.everymac.com/systems/apple/emac/index-emac.html)

If yours has an nvidia card, adjustments have to be made to this file, such as changing the driver to "nv" among other things - if this is the case.  There is also the ati radeon 7500 and 9200 which might need different settings.

Yep, but because of Intrepid's new X server, if it doesn't work with all of this, I'd be tempted to pare it down to just this (as a quickie template until you determine your video card!)

```

Section "Module"
Disable "dri"
Disable "glx"
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 71-73
VertRefresh 70-140
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
EndSection
```

Let's find out what video card you have and you can move on from there if further edits need to be made.

---

### Post by Brii on 2008-11-22
> **stream303 said:**
> First thing to do is determine exactly what your model is, because the video cards differ:

[http://www.everymac.com/systems/apple/emac/index-emac.html](http://www.everymac.com/systems/apple/emac/index-emac.html)

If yours has an nvidia card, adjustments have to be made to this file, such as changing the driver to "nv" among other things - if this is the case.  There is also the ati radeon 7500 and 9200 which might need different settings.

Yep, but because of Intrepid's new X server, if it doesn't work with all of this, I'd be tempted to pare it down to just this (as a quickie template until you determine your video card!)

```

Section "Module"
Disable "dri"
Disable "glx"
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 71-73
VertRefresh 70-140
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
EndSection
```

Let's find out what video card you have and you can move on from there if further edits need to be made.


I'm pretty sure its this one [http://www.everymac.com/systems/apple/emac/stats/emac_1.0.html](http://www.everymac.com/systems/apple/emac/stats/emac_1.0.html)

Im trying to install 8.10 btw

thank you

---

### Post by stream303 on 2008-11-23
Cool!  Looks like this info should get you going.

Since you are installing Intrepid, I wouldn't be surprised if it failed to find your cdrom drive during install.  When/if it does, just get to a virtual terminal via CTRL-ALT-F2, login, and type

```
sudo modprobe ide-scsi
```

Now, CTRL-ALT-F1 to get back to the installer.  Just back out of the dialog telling you about the error to the point where you can tell it to detect the cdrom drive again - and now all should go well.

---

### Post by Brii on 2008-11-23
> **stream303 said:**
> Cool!  Looks like this info should get you going.

Since you are installing Intrepid, I wouldn't be surprised if it failed to find your cdrom drive during install.  When/if it does, just get to a virtual terminal via CTRL-ALT-F2, login, and type

```
sudo modprobe ide-scsi
```

Now, CTRL-ALT-F1 to get back to the installer.  Just back out of the dialog telling you about the error to the point where you can tell it to detect the cdrom drive again - and now all should go well.

i type in sudo modprobe ide-scsi and it said that bash: sudo not found

i think its is because i didnt "log in" how do you log in

---

### Post by crapple on 2008-11-23
You don't need 
```
sudo modprobe ide-scsi
```
You need
```
modprobe ide-scsi
```

Hope this works for you. If you need anymore help I also have an emac.

---

### Post by stream303 on 2008-11-23
Oops, sorry about that - Crapple's right about not needing sudo in this instance.

---

### Post by Brii on 2008-11-23
> **crapple said:**
> You don't need 
```
sudo modprobe ide-scsi
```
You need
```
modprobe ide-scsi
```

Hope this works for you. If you need anymore help I also have an emac.

well i got it to install but I'm still not getting to the desktop since you have a emac i was wondering if you can show me your /etc/X11/xorg.conf file please

if your running 8.10

---

### Post by Brii on 2008-11-23
> **stream303 said:**
> First thing to do is determine exactly what your model is, because the video cards differ:

[http://www.everymac.com/systems/apple/emac/index-emac.html](http://www.everymac.com/systems/apple/emac/index-emac.html)

If yours has an nvidia card, adjustments have to be made to this file, such as changing the driver to "nv" among other things - if this is the case.  There is also the ati radeon 7500 and 9200 which might need different settings.

Yep, but because of Intrepid's new X server, if it doesn't work with all of this, I'd be tempted to pare it down to just this (as a quickie template until you determine your video card!)

```

Section "Module"
Disable "dri"
Disable "glx"
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 71-73
VertRefresh 70-140
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
EndSection
```

Let's find out what video card you have and you can move on from there if further edits need to be made.

i installed it and put that in and im getting these errors

(EE) Problem parsing the config file

(EE)Error parsing the config fil

THANK YOU =] btw


FYI the horiz and vert setting you gave me made eveythin blur so i changed it to 
HorizSync 30-112

VertRefresh 50-160

and it didnt look all blury but still getting the gray box with thoe errors up there

---

### Post by stream303 on 2008-11-24
> **Brii said:**
> i installed it and put that in and im getting these errors

Can you verify your video card with

```
lspci
```

Just to make sure.  It should show up there as an nvidia, ati, etc.  Just to doublecheck...

Also, to help cut down on typos, remove the "Module" section completely.  We can deal with that later if need be.

It is also unlikely that you'll ever want anything less than a 24bit depth, and is specified as the default anyway.  To cut down on even more possible typos, we can shorten it:

```
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Monitor "iMac"
DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1280x960" "1152x870" "1024x768"
  EndSubSection
EndSection
```

> FYI the horiz and vert setting you gave me made eveythin blur so i changed it to 
HorizSync 30-112
VertRefresh 50-160

I'd stick to the previous ones since those are the ones that I've seen on nearly all emacs to work properly.  Where did you get those freqs?

You aren't on an external monitor are you?  I've heard of emacs getting hacked with an external display connector/port before that is unsupported...

Maybe by removing the Modules section, and shortening the Screen section it won't make Intrepid barf. :)

AND just so we don't get our wires crossed, the monitor type should be "eMAC, not "iMac" - I'm assuming we're dealing with your Emac.  Not that this would break things, but anyone doing a quick read might try to apply this to their G3 iMac for instance by accident....

---

### Post by Brii on 2008-11-25
> **stream303 said:**
> Can you verify your video card with

```
lspci
```

Just to make sure.  It should show up there as an nvidia, ati, etc.  Just to doublecheck...

Also, to help cut down on typos, remove the "Module" section completely.  We can deal with that later if need be.

It is also unlikely that you'll ever want anything less than a 24bit depth, and is specified as the default anyway.  To cut down on even more possible typos, we can shorten it:

```
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
Monitor "iMac"
DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1280x960" "1152x870" "1024x768"
  EndSubSection
EndSection
```



I'd stick to the previous ones since those are the ones that I've seen on nearly all emacs to work properly.  Where did you get those freqs?

You aren't on an external monitor are you?  I've heard of emacs getting hacked with an external display connector/port before that is unsupported...

Maybe by removing the Modules section, and shortening the Screen section it won't make Intrepid barf. :)

AND just so we don't get our wires crossed, the monitor type should be "eMAC, not "iMac" - I'm assuming we're dealing with your Emac.  Not that this would break things, but anyone doing a quick read might try to apply this to their G3 iMac for instance by accident....

YEah its an ati i double checked

and i did everything you said i got rid of the modules section and shorted the other one

and still no go

Doesnt work =\

---

### Post by stream303 on 2008-11-25
Wow, frustrating huh?  I wish I could say I see something that jumps out.

Do you have any objections to trying 7.10 Gutsy again?  Although support is nearing the end-of-life for it, it doesn't mean that the software stops working. :)  If you were to try it, see the note about the busybox shell prompt you'll encounter:

[https://wiki.edubuntu.org/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.edubuntu.org/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot)

These older releases with their classic xorg.conf with all the details filled in might be the way to go for now, where all you have to do is swap a few values around.

In fact, you could try Ubuntu Dapper 6.06x which still has update support.  However lately I can heartily recommend Debian Etch 4.0r5 Stable powerpc for that machine as a first install too:  (CD-1 is all you need)

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

With the emac, nearly all installs need manual configuration, but at least with Debian, you won't have to mess about with repos changing, cd-roms not being recognized, busybox shells, etc. :)  I'm not ragging on Ubuntu, but you have really hung in there through all the tough stuff, so Debian might be a walk in the park. :)

quickie notes:
[http://ubuntuforums.org/showthread.php?t=988449](http://ubuntuforums.org/showthread.php?t=988449)

---

### Post by Brii on 2008-11-26
> **stream303 said:**
> Wow, frustrating huh?  I wish I could say I see something that jumps out.

Do you have any objections to trying 7.10 Gutsy again?  Although support is nearing the end-of-life for it, it doesn't mean that the software stops working. :)  If you were to try it, see the note about the busybox shell prompt you'll encounter:

[https://wiki.edubuntu.org/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.edubuntu.org/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot)

These older releases with their classic xorg.conf with all the details filled in might be the way to go for now, where all you have to do is swap a few values around.

In fact, you could try Ubuntu Dapper 6.06x which still has update support.  However lately I can heartily recommend Debian Etch 4.0r5 Stable powerpc for that machine as a first install too:  (CD-1 is all you need)

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

With the emac, nearly all installs need manual configuration, but at least with Debian, you won't have to mess about with repos changing, cd-roms not being recognized, busybox shells, etc. :)  I'm not ragging on Ubuntu, but you have really hung in there through all the tough stuff, so Debian might be a walk in the park. :)

quickie notes:
[http://ubuntuforums.org/showthread.php?t=988449](http://ubuntuforums.org/showthread.php?t=988449)

alright ill try debainan

i wont be on the forum for a while cuz im going out of town for thanksgiving but ill come back and give you an update thanks and happy thanksgivein =p

---

