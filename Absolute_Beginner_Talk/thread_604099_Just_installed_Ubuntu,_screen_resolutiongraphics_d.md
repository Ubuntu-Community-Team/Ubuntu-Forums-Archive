---
title: "Just installed Ubuntu, screen resolution/graphics don't look right"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-05
Very new to Linux/Ubuntu.
Just installed 7.10

Something not right with the graphics/screen resolution - can't put my finger on it.
I'm being told in Screen Resolution I'm getting 1280 x 800 which I think was my setting in XP. But dialog boxes look rather large on my screen- perhaps that's just the way Ubuntu is configured.

More cause for concern though is text on web pages- looks very different (and not as good as on Windows- see attached screenshot of ebay for example- the categories on the left hand side of the page look like they're in a strange font.

And above all, images don't look at all sharp or detailed. It's all rather fuzzy and unattractive.

I've searched a bit on google and in these forums and there's various talk about ATI drivers.
I think I have an ATI Radeon graphics card, but now don't know how to find out which one.
Am I missing drivers for it?
If so, please can someone post (very simple step by step instructions for a total newbie/non-techie) how I fix this?
Many thanks

---

### Post by Flying caveman on 2007-11-05
you could try opening up a terminal.

Applications>Accessories>Terminal

and type (or paste) this ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

enter you password.  

see if it lets you select a higher resolution (use up and down arrows and space bar to select)

enter

Not sure if you need to reboot or maybe just log out and log back in before resolutions become available

---

### Post by Tyke91 on 2007-11-05
type the command

```
sudo lshw | less
```in order to check your system stats (graphics card - etc)

then go to System>Administration>Restricted Drivers Manager (in the menu bar) and select your ATI driver if it isn't already. once that is ready, restart your compy.

---

### Post by wPwLUi3N on 2007-11-05
your screen shot looks fine tome.

Maybe you need to install the appropriate ATI DRiver and also i think your on motherboard graphic card doesnot support the resolution you are demanding but possibly your ATI CARD can.

Also the control window should be available to you to set resolution even through you ATI Driver package setting option.

I use nvidia so i am not quite sure and get comfortable 1400 X 900 resoultion.

---

### Post by 01steven on 2007-11-07
I'm still convinced things aren't 100% right with the way my screen looks.
It might be difficult for anyone other than me to see, but generally everything looks very 'soft', almost blurred, whereas previously in Windows XP it was all very crisp, clean and clear.
And when I look at some images on screen they look a bit patchy.

But other places I look, photos for example, don't look bad.
And it is telling me I'm getting 1280 x 800 which is what I was getting in XP.

So I'm just not sure what's happening...

---

### Post by Hatchetfish on 2007-11-07
what make and model is your monitor?  just on your description of the appearance, it really does sound like you're not getting the native resolution of the screen.

---

### Post by Hatchetfish on 2007-11-07
i just checked the size of your screenshot, and it's not 1280x800, it's 1280x750.  can you summarize what system>preferences>screen resolution says you're getting, and what system>administration>screen and graphics says?

(if you like a screenshot of each would work too.  alt+printscreen will take a shot of just the focused window and save some bandwidth btw)

---

### Post by tombott on 2007-11-07
The reason your web browsing looks different is due to Microsoft fonts.

Try installingmsttcorefonts to see if this improves the display

```
sudo apt-get install msttcorefonts
```

---

### Post by 01steven on 2007-11-07
Here are the screenshots of the settings as requested.

---

### Post by orangeman on 2007-11-07
I've seen a few issues with ATI cards while browsing the forum, but I have an ATI as well and without having to change any settings or install any drivers I automatically get the same resolution as I use in Vista 1280 x 1024 (17inch iiyama CRT monitor).
Of course, I haven't got to trying anything in 3D as I normally work with in Vista so issues might arise.

---

### Post by 01steven on 2007-11-07
This is my graphics card apparently:
Radeon RV250 [Mobility FireGL 9000]
If this is of any use to anyone who can help me...

---

### Post by Hatchetfish on 2007-11-07
well, crap. ;)  I'm stuck at this point.  The 'screen and graphics' settings control is new as of ubuntu 7.10, and i haven't figured out how to read /etc/X11/xorg.conf since they started using the new setup, so we need someone more familiar with the intricacies of that.  I'm very suspicious of 'screen and graphics' though, this is the third time i've seen it not actually setting things to the resolution it says it is.  Unfortunately, you really can't just remove it and go back to the old way. (and aside from it not quite working right, that's not something you should probably do unless you enjoy messing with large plain text config files.  'screen and graphics' -is- a step in the right direction, but I'm thinking it's a bit of a stumble for now.)

---

### Post by 01steven on 2007-11-07
OK well let's hope someone else on here will be able to help.
Regards

---

### Post by 01steven on 2007-11-08
Does anyone have any further suggestions please?

---

### Post by Maestro23 on 2007-11-08
> **01steven said:**
> Does anyone have any further suggestions please?

What is the output of:

> fglrxinfo

Also, post your /etc/X11/xorg.conf

> cat /etc/apt/xorg.conf

---

### Post by DawnDisciple on 2007-11-08
My graphics are somewhat iffy, but I put that down to there being no Linux drivers for my Monitor.  It did help when I changed the font to compatible LCD font.

It is strange if I change my monitor from plug and play to 1280x1024 LCD the screen goes bonkers, yet my monitor is a LCD with native res 1280x1024.

---

### Post by 01steven on 2007-11-10
> **tombott said:**
> The reason your web browsing looks different is due to Microsoft fonts.

Try installingmsttcorefonts to see if this improves the display

```
sudo apt-get install msttcorefonts
```

This definitely made a difference to the fonts.
For anyone who's interested compare this screenshot to the one in my earlier posts- look at the ebay category names on the left hand side to see the difference.

---

### Post by 01steven on 2007-11-10
Maestro23- in answer to your questions:

> **Maestro23 said:**
> What is the output of:

steven@steven-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
steven@steven-laptop:~$ 


Also, post your /etc/X11/xorg.conf

steven@steven-laptop:~$ cat /etc/apt/xorg.conf
cat: /etc/apt/xorg.conf: No such file or directory
steven@steven-laptop:~$ 

Please can you advise?
Didn't want to install without someone on here confirming it was safe.

Regards

---

### Post by tukuyomi on 2007-11-10
```
steven@steven-laptop:~$ cat /etc/apt/xorg.conf
cat: /etc/apt/xorg.conf: No such file or directory
steven@steven-laptop:~$ 
```
you mistyped your command here
```
$ cat /etc/X11/xorg.conf
```(with uppercase X in X11)

---

### Post by 01steven on 2007-11-10
OK just copied and pasted.
What about installing 'fglrxinfo'?

---

### Post by 01steven on 2007-11-10
steven@steven-laptop:~$  cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection
steven@steven-laptop:~$

---

### Post by 01steven on 2007-11-10
Please can someone out there have a look at what I've posted and try and help me?
Many thanks

---

### Post by matthewcraig on 2007-11-10
You're bumping all your threads a bit often, 01steven.... I believe the FAQ says to resort to bumps after 24 hours.

---

### Post by Maestro23 on 2007-11-10
> **matthewcraig said:**
> You're bumping all your threads a bit often, 01steven.... I believe the FAQ says to resort to bumps after 24 hours.

Edit.

---

### Post by 01steven on 2007-11-10
> **matthewcraig said:**
> You're bumping all your threads a bit often, 01steven.... I believe the FAQ says to resort to bumps after 24 hours.

OK sorry- didn't realise there were rules about this, but now I know I'll behave!

---

### Post by 01steven on 2007-11-11
Anyone out there who can help?
Thanks

---

### Post by 01steven on 2007-11-11
Recently installed Ubuntu.
Not sure my graphics/screen resolution is configured properly.

Things look quite fuzzy on screen- nowhere near as sharp as they did in Windows.
Is there a way of telling if I need to reinstall drivers for my graphics card?

---

### Post by maharbA on 2007-11-11
Welcome to the community!

What video card do you have? Are you using Gutsy (7.10)? Are you using Ubuntu, Kubuntu, Xubuntu?

"Fuzzy" is, well, a bit fuzzy. If you could post some screenshots, that would help. Just hit the "print screen" button on your keyboard or go to APPLICATIONS>ACCESSORIES>TAKE SCREENSHOT

There are lots of ways we can help, and the more info we have, the better.

---

### Post by 01steven on 2007-11-11
Hi
Am using latest version of Ubuntu 7.10 Gutsy.
Attached screenshot- no doubt you'll say it looks fine!
But I know it is definitely not like it was in Windows.
I can tell you more about my system set up if you tell me what you need to know...

---

### Post by 01steven on 2007-11-11
Oops- screenshot didn't attach first time.
Proof that I'm a newbie!

---

### Post by skymera on 2007-11-11
looks fine to me :)

---

### Post by 01steven on 2007-11-11
haha
could have predicted that.

Like I say, I KNOW it's not right, as it was much clearer in Windows.

Please can someone advise how to check I have things configured properly?

---

### Post by FuturePilot on 2007-11-11
What graphics card do you have and do you know what the correct settings are?
Refresh rate, resolution, etc....

---

### Post by dampbuffalo on 2007-11-11
yeah i have a nvidia geforce go 6150 and the highest in resoluition i can go is 800x600 and im using ubuntu 7.10:confused:
please help

---

### Post by Maestro23 on 2007-11-11
> **01steven said:**
> haha
could have predicted that.

Like I say, I KNOW it's not right, as it was much clearer in Windows.

Please can someone advise how to check I have things configured properly?

Why are you making duplicate threads about the same issue? Here's your 3-page thread on the same issue.

[http://ubuntuforums.org/showthread.php?t=604099](http://ubuntuforums.org/showthread.php?t=604099)

Just as excessive bumping are is not allowed, so is making duplicate threads about the same issue.

---

### Post by 01steven on 2007-11-11
Some information from an earlier thread which didn't result in anyone helping unfortunately:

[http://ubuntuforums.org/attachment.php?attachmentid=49460&d=1194474382](http://ubuntuforums.org/attachment.php?attachmentid=49460&d=1194474382)
[http://ubuntuforums.org/attachment.php?attachmentid=49461&d=1194474382](http://ubuntuforums.org/attachment.php?attachmentid=49461&d=1194474382)

Radeon RV250 [Mobility FireGL 9000]

steven@steven-laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection
steven@steven-laptop:~$

---

### Post by FuturePilot on 2007-11-11
Have you installed the driver? System>Administration>Restricted Driver Manager.

---

### Post by 01steven on 2007-11-11
> **FuturePilot said:**
> Have you installed the driver? System>Administration>Restricted Driver Manager.

Nothing in there to install.

---

### Post by maharbA on 2007-11-12
Nowadays I've found that I rarely have to delve into xorg.conf

Do you have the restricted driver installed? I don't think you do.
If you're using Feisty or Gutsy (7.04 or 7.10) open the Restricted Drivers Manager (SYSTEM>ADMINISTRATION>RESTRICTED DRIVERS MANAGER ...  I think) and see what it says.

Try enabling the restricted driver. Then, if you're using Gutsy, go to SYSTEM>PREFERENCES>SCREEN RESOLUTION and set it to your desired resolution.

Also, check your font display settings (under SYSTEM>PREFERENCES I believe) and make sure that's set how you like it.

---

### Post by TeaSwigger on 2007-11-12
> **dampbuffalo said:**
> yeah i have a nvidia geforce go 6150 and the highest in resoluition i can go is 800x600 and im using ubuntu 7.10:confused:
please help

Hello, find the "restricted drivers manager" referenced to previously. See if it has anything. Easiest route first :)

> **01steven said:**
> Some information from an earlier thread which didn't result in anyone helping unfortunately:

[http://ubuntuforums.org/attachment.php?attachmentid=49460&d=1194474382](http://ubuntuforums.org/attachment.php?attachmentid=49460&d=1194474382)
[http://ubuntuforums.org/attachment.php?attachmentid=49461&d=1194474382](http://ubuntuforums.org/attachment.php?attachmentid=49461&d=1194474382)

Radeon RV250 [Mobility FireGL 9000]

steven@steven-laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection
steven@steven-laptop:~$

One observation, two suggestions: 
- It says Generic Monitor. 

- Perhaps the resolution and/or refresh rate is too high or too low.
- Perhaps if you can get it to identify the exact monitor it may work better.

---

### Post by 01steven on 2007-11-12
> **maharbA said:**
> Do you have the restricted driver installed? I don't think you do.
If you're using Feisty or Gutsy (7.04 or 7.10) open the Restricted Drivers Manager (SYSTEM>ADMINISTRATION>RESTRICTED DRIVERS MANAGER ...  I think) and see what it says.


See attached screenshot re: restricted drivers. Only one - a modem driver, and it's enabled.

---

### Post by 01steven on 2007-11-12
> **TeaSwigger said:**
> Hello, find the "restricted drivers manager" referenced to previously. See if it has anything. Easiest route first :)



One observation, two suggestions: 
- It says Generic Monitor. 

- Perhaps the resolution and/or refresh rate is too high or too low.
- Perhaps if you can get it to identify the exact monitor it may work better.

How do I change refresh rate?
How do I get it to identify the exact monitor?

---

### Post by jay1097 on 2007-11-12
Hey
i checked out ur screen shot and everything looks normal lol. But i had a similar problem as yours. i was using a ATi x1550 and i found that my screen didn't look quite 'right', although the resolution was fine, the image itself wasn't clear. Anyway to make a long story really long i got a nvidia 8600gt and everything looked a lot better. So it could be that ur grafics card is causing the display problem and the only fix is an upgrade (which if u have a laptop isn't much of an option). Also like other people said install the restricted drivers and try looking in the more advanced forums because they often have answers for very specific problems.
Anyway good luck:KS

---

### Post by Meuro on 2007-12-01
hey

I'm having the same problem.  Everything looks fuzzy/blurry.  I've installed the ms fonts and made sure the NVidia binary X.Org drivers where installed.

Ive set my screen resolution as high as it'll go which is 1280x1024.  The refresh rate is 60hz which is the only option it gives.

I have a 19" illyama tft and a inno3d 7600 graphics card.

The lack of sharpness is beginning to seriously bug me.  Please help :(

---

### Post by Flying caveman on 2007-12-01
Has anybody considered that 01 steven's monitor might not be 1280x800,  I know that on my laptop I had to edit the xorg.conf to show my native resolution of 1680x1050,  

Also, if its just a separate LCD panel sometimes you need to use the buttons on the monitor itself to adjust it.   (autio-adjust button?)

---

### Post by Meuro on 2007-12-02
actually i second caveman.  i was having this problem but i just did a reset on my monitor and it then auto adjusted itself.  made such a HUGE difference!

---

