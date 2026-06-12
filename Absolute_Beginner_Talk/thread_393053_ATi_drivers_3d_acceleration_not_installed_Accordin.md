---
title: "ATi drivers 3d acceleration not installed? According to cedega?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-03-24
hi, well nearly 6months ago when i last ran ubuntu 6.0.6 ATi driver installation attempts screwed up my install.so what i NEED is SIMPLE and i MEAN simple steps of what exactly to do and how with screenshots preferably:P
I don't want an overcompliacated link just something that i can follow and pick up and do without screwing everything up.

i have a asus 9600xt 128mb...

so What Do I Do... and  HOW!

cheers

---

### Post by jbayone on 2007-03-24
If you want something simple, use the Envy script.  You don't have to do much at all, except choose a couple of options.  A link is in my signature.

---

### Post by freebird54 on 2007-03-24
Envy is a great choice  *IF* you haven't already tried 4 or 5 other things :)

ATI cards actually work pretty well - they don't deserve QUITE so bad a rep as they have around here!

---

### Post by zekopeko on 2007-03-24
i used this when i had ATI.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

just follow the first part (editing some system files) and then use method 2.

---

### Post by keef247 on 2007-03-24
would i be able to run beryl smoothly?
amd mobile xp-m 2400 @ 2.2ghz with 1gb ram asus ati 9600xt 128mb... will post experiences later when i try drivers.

---

### Post by freebird54 on 2007-03-24
Beryl runs reasonably well on my setup - certainly well enough to show off to Mac and Win users :D

I am using the XGL/Beryl setup as described in a number of Howtos - it is necessary to use XGL, I understand, if you are using the fglrx driver.  That means disabling AIGLX, but I think Envy does all that for you when it works anyway.  Happy cube rotation!

---

### Post by keef247 on 2007-03-24
nice! that sounds reallly encouraging. I'd like to thank everyone for their support and input especially freebird54.ubuntu is defineataly the best choice I've made on my pc!
EDIT: Forgot to ask... Is there anyway I can backup/restore ubuntu if I screw this up?
cheers yet again!

---

### Post by freebird54 on 2007-03-24
Lots of ways to restore it - not likely to need a full backup.  One useful idea is to make a copy of xorg.conf before beginning though...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

just in case!

---

### Post by keef247 on 2007-03-24
I'm trying to install ATi with envy but I'm getting some kind of error popup? i downloaded the first one i think it maybe for 6.10. (envy) but it installed and all?link to one that i should be using for 6.0.6?
cheers

---

### Post by freebird54 on 2007-03-24
Not sure what the problem is but...

Which version of Ubuntu are you using? 6.06? 6.10?  Kubuntu? Xubuntu?

Did you get Envy from here?  **[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)**

Inquiring minds want...... :)

BTW:  sorry for slow responses - watching the hockey games too.... :D

---

### Post by keef247 on 2007-03-24
6.0.6 i have...
yeah i used that link apparently they've disabled 6.0.6 for 9.1?
so im upgrading my distro to 6.10 now... and then i'll use the 6.10
did try the older 8.whatever ones and made my pc restart to a login ttyl1?
and then wouldn't do anything so had to power off! no worries enjoy the game boss.

---

### Post by keef247 on 2007-03-25
ok just installed envy's ATi drivers for my 9600xt... now i can only select 75/60hz... it runs at 70hz...
how do i change this as its centered around black space in my monitor now:@
cheers. also how do i know if their working?
its a dell DELL D1226H or something like that i can't remember.

---

### Post by keef247 on 2007-03-25
anyone help me now i have this problem...
[http://ubuntuforums.org/showthread.php?p=2350337#post2350337](http://ubuntuforums.org/showthread.php?p=2350337#post2350337)

---

### Post by keef247 on 2007-03-25
bump

---

### Post by keef247 on 2007-03-25
just installed envy's ATi drivers for my 9600xt.. and setting up cedega and apparently oss sound and 3d acceleration arent installed or setup properly or something:S
how do i set them up? surely envy would have done that i did the automated install...
HELP!

---

### Post by keef247 on 2007-03-25
BUMMMMMMMMMMMP cmon!!

---

### Post by keef247 on 2007-03-25
anyone?

---

### Post by freebird54 on 2007-03-25
Sorry for the slow response - have to sleep sometime!

Sounds like your setting are not yet optimal - but I don't know your monitor specs as yet.  Probably what is needed is to edit the /etc/X11/xorg.conf file.  Please post that file here as follows...

Open up an Applications->Accessories->Terminal.  in the window, enter

cat /etc/X11/xorg.conf

Use the slider to scroll  up to the start of the output, highlight it with the mouse, and either Edit->Copy or <ctrl><shift>C to pick it up.  Click with the message you are editing and <ctrl>v.  While it is still highlighted (or highlight it again) click on the # in the menus at the top of the message editor to 'put it in a box'.  This goes for any posting of output we'll need.  The result will look similar to this:

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
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Radeon 9550"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon 9550"
        Monitor    "Samsung_900iFT"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```


Once we get to editing this, we will **NEED** the specs for your monitor - so perhaps you can dig them up, or google them if necessary.  If the settings for the monitor are 'off' too far, we could blow it up!

Ok - that should get things moving again...

---

### Post by machoo02 on 2007-03-25
Can you post the output of these commands from the terminal:```
glxinfo | grep "direct rendering"

fglrxinfo
```

---

### Post by keef247 on 2007-03-25
ok just installed envy's ATi drivers for my 9600xt... now i can only select 75/60hz... it runs at 70hz...
how do i change this as its centered around black space in my monitor now:@
its a dell DELL D1226H. Upon Installing Cedega i ran the test... seems OSS sound isn't working and neither is 3d acceleration... WHAT WENT WRONG? I just used envy to auto install the drivers:S surely they should work? HOW do I fix this? Also after playing counter-strike i get no sound? and upon exit mucks up my resolution and puts it back to the 75hz which doesn't display properly! I'm having to use 60hz at the moment.
cheers for any help you can give!

---

### Post by keef247 on 2007-03-25
> **machoo02 said:**
> Can you post the output of these commands from the terminal:```
glxinfo | grep "direct rendering"

fglrxinfo
```

yep!

root@pc:~# glxinfo | grep "direct rendering"
direct rendering: Yes
root@BIG-SHELL:~# 
root@BIG-SHELL:~# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by keef247 on 2007-03-25
hi, cheers mate:) your so helpful!:KS :) 
```
this is what i have:
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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
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
Identifier "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "DELL D1226H"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
Monitor "DELL D1226H"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
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
EndSection

Section "DRI"
Mode 0666
EndSection
```

erm its a DELL D1226H does 1600x1200 @75hz optimal but i swear it does it at 70hz in windows not 75 as it will not do 75 in either windows or linux... so need 70hz please. the specs are [http://support.dell.com/support/edocs/monitors/59119/](http://support.dell.com/support/edocs/monitors/59119/)

thankyou so much!

---

### Post by freebird54 on 2007-03-25
OK  I see a couple of things here.  First off - it is NOT using the new driver you just installed.  It is called fglrx.  Make your Device section look this..

```
Section "Device"
	Identifier "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Driver      "**fglrx**"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

```

Notice the change to fglrx.  You will also likely the need the other new lines as well. Then let it know what your monitor is supposed to be able to do.  Change Monitor section to read like:

```
Section "Monitor"
	Identifier "DELL D1226H"
[B]        HorizSync    30.0 - 95.0
        VertRefresh  50.0 - 160.0
 [/B]       Option      "DPMS"
EndSection
```

Then a couple of little things to add in new:


```
Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

After you make these changes, (which you have made with **gksudo gedit /etc/X11/xorg.conf **) save and exit the file - then hit **<ctrl><alt><backspace> **to reset your X session.  Hopefully it comes up better, or at least can be changed to your choice with System->Preferences->Screen Resolution.

One last thing - after this, open a terminal and run fglrxinfo and post the result here - there MAY be another edit required elsewhere, depending on what it says :)

---

### Post by keef247 on 2007-03-25
oh and do you know how to change the default hz rate on the login screen.as its still 75hz:@

---

### Post by freebird54 on 2007-03-25
Have you set it to 70 in System->Preferences->Screen Resolution?  As far as I know it picks it up from there when it's been set.  Nothing on my system TELLS me what rate its at login - but it appears not to be 60 (which pulses a bit on our electrics).

---

### Post by machoo02 on 2007-03-25
Well...based on your terminal output, you do have 3d acceleration all set up and working.  I don't know too much about cedega, so I'm not sure what could be the problem with it.  You could try posting something like this over in the Gaming section of the forum

---

### Post by keef247 on 2007-03-25
wierd:S any app/game for linux i could download thats small to see if this is true or a terminal command that would do a render utilising it or something like that.haha and could you link me to the gaming section i got comfused finding it:$
cheers again for your help!

---

### Post by keef247 on 2007-03-25
nah its default is 75...
oh and the above info i provided could you possibly make me a new xorg.conf and paste it here with a custom hz setting from a modeline site?please!

---

### Post by freebird54 on 2007-03-25
Sorry - haven't played with modelines yet - due to lack of need!  I'll look at it - but the chances are better that you'll find one before I do...

---

### Post by keef247 on 2007-03-25
cheers mate.be amazing if you could try and come up with something for me:)
cheers for being so helpful too.

---

### Post by machoo02 on 2007-03-25
From the front page of the forums, look in the "Other Support Categories" (about halfway down the page) for the 'Gaming and Leisure' link.

---

### Post by keef247 on 2007-03-26
edited my xorg.conf and added the lines including fglrx etc and the line for my monitor. still cedega tells me no 3d acel and login screen is at stupid 75hz again:@
how do i make it 70hz 1600x1200 as default...
and what do i do now about xorg.conf you meintioned it might need another line...

---

### Post by freebird54 on 2007-03-26
If you got all the edits I posted for you - should be all of it.  If you still run into cedega probs - better to move the post over to gaming etc forum - much more expertise there! (I do my gaming on an Amiga... don['t need no Intel compat for that!)

---

### Post by keef247 on 2007-03-26
yeah all edits done:( still doing it. how would i be able to know if its working?and app or game you know of to test with?
cheers by the way for everything.and amiga haha badass.

---

### Post by ikonia on 2007-03-27
Try the advanced options of glxgears, 

They normally tell you if DRI is running and even what frames per second.

---

### Post by keef247 on 2007-04-20
hmmm after booting an old 6.0.6LTS live cd turns out 1600x1200 on default driver at 75hz works fine... so why is envy mucking it up?
any simple guide to install the ATi driver manually?

---

