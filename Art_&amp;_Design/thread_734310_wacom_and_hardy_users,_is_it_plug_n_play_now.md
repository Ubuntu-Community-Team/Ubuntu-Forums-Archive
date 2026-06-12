---
title: "wacom and hardy users, is it plug n play now?"
date: 2008-03-24
forum: Art &amp; Design
---

### Post by days_of_ruin on 2008-03-24
Thinking about getting a wacom tablet but don't want to have to spend
a week getting it setup right.So if you are using hardy heron beta, is 
it just plug in it and it works?

---

### Post by days_of_ruin on 2008-03-25
uuhh *bump*

---

### Post by Ralphie on 2008-03-25
I will be installing the  beta tonight most likely, and will report back with how it works.

---

### Post by stephantom on 2008-03-26
My problem with my tablet was always that I had to have it plugged in before X started. Then everything would work flawlessly. If I'd plug it in during an active session, the tablet would only work in relative mode and only if I touched down on the tablet (otherwise I could hover the pen over the surface and move the cursor about).
I don't think/know whether this has been fixed (i.e. true plug/play), I'll have to try it this afternoon.

---

### Post by Ralphie on 2008-03-26
My experience has always been the same as stephantom's.

I messed with it shortly before work today, and it seems to be acting the same, but I might have figured out a way to get plug and play to work. I will mess with it after work and we'll see where it gets us!

---

### Post by days_of_ruin on 2008-03-26
So if you plug it in before starting X it has full functionality?
If thats true I'm cool with it.

---

### Post by Ralphie on 2008-03-26
Yes thats how you have to do it but it works fine like that.
I noticed in the removable devices tab (or whatever its called) in ubuntu there is a place where you can define a script or application to run when a wacom is plugged in. I wonder if there is something we can write or put there that will allow for it to plug and play.

That is what I was going to mess with tonight, anyone is welcome to help out.

---

### Post by lyceum on 2008-03-26
> **Ralphie said:**
> Yes thats how you have to do it but it works fine like that.
I noticed in the removable devices tab (or whatever its called) in ubuntu there is a place where you can define a script or application to run when a wacom is plugged in. I wonder if there is something we can write or put there that will allow for it to plug and play.

That is what I was going to mess with tonight, anyone is welcome to help out.

Good info, Thanks!

---

### Post by Ralphie on 2008-03-26
After messing some more with it, I've found two things, one, it doesnt seem to like 8.04 right now, but I saw a bug filed for it. I think it is believed there is not a sufficient driver released yet, but it is hoped there will be by the official release of 8.04. 

Also, I have not messed with a script yet, but I have found a quick work around, which is to restart X (ctrl+alt+backspace) after plugging in the wacom, and it will be recognized as if you restarted. This saves a lot of time!

---

### Post by z0r on 2008-04-01
My Wacom tablet is working fine in Hardy with the latest packages. I still have to have it plugged in before X starts.

There has been one big improvement: the tablet and my laptop's touchpad used to interfere with each other. In Gutsy I always had to unplug my tablet, plug it back in and restart X before logging in. Now that has been fixed, so I just leave my tablet plugged in all the time.

---

### Post by Ioky on 2008-04-05
I get my tablet work, but one fore sometime. not all the time. I don't know why, it was always put in system. so I don't know what wrong with it. but yeah, I don't know way they don't make drive for Linux. Feel kind of not fair. haha I mean even Hollywood use Linux for movie, and stuff. You know like dream work, and such. Funny and non sense, haha

---

### Post by gaminggeek on 2008-04-05
how did you get it to go mine only works in the mode where you have to put the pen to the tablet to move the mouse

---

### Post by pibach on 2008-04-05
Does this require to download and compile latest drivers from linux-wacom? And does it work on Tablet PC (these have wacom digitizer connected via serial)?

---

### Post by TygerFish on 2008-04-06
I've been running Hardy Beta and it hasn't treated my Wacom any differently than it did in Gutsy: relative mode is plug and play, but I had to edit my xorg.conf file to get the stylus to do absolute mode, be pressure sensitive, and otherwise behave properly.

---

### Post by red_Marvin on 2008-04-06
> **TygerFish said:**
> I've been running Hardy Beta and it hasn't treated my Wacom any differently than it did in Gutsy: relative mode is plug and play, but I had to edit my xorg.conf file to get the stylus to do absolute mode, be pressure sensitive, and otherwise behave properly.

Could you please post your xorg.conf, or maybe a link on how to configure it?

---

### Post by oki-vino on 2008-04-07
Yes I would like to know what you put in xorg to do those things Tyger

---

### Post by Olozhika on 2008-04-07
Hi there, I have a Wacom tablet and it has worked with Kubuntu 6.06, 7.10 and Ubuntu 7.04, 7.10 and 8.04
The most complicated part of the installation was getting the usb plug the right way round!

---

### Post by red_Marvin on 2008-04-07
Never mind I got it working by repeating the steps described [here]("http://ubuntuforums.org/showthread.php?t=740134").

---

### Post by reya276 on 2008-04-07
That's funny, because my wacom bamboo fun does not work at all I don't even have the section where it should be in my xorg.conf file, so what are you guys doing that I'm not. With gutsy I compile the driver and got it working that way but now nothing seems to get this working. if anyone has an answer please help as I don't want to go back to using PS/Windows to use it.

---

### Post by eel on 2008-04-10
My et-4050 isn't working although i configured my xorg.conf.
I don't get what the problem is so i'll just keep searching. I remember it looked different when i had gutsy so i'll try to find the howto i used back then.

---

### Post by eel on 2008-04-11
from 'not working' in the sense of 'not working like it should' i now got to not working period. I have in- re- and uninstalled the wacom-tools and wacom-xorg files 5 times now.
What imo might be part of the problem is that my xorg.conf doesnt get changed when i install wacom-tools or wacom-xorg. I remember this happening before in gutsy, where i just manually added the lines about the wacom and things worked just fine. Not this time though, everytime i fiddle with the xorg.conf i get hell to pay (freezes, login sound getting stuck and the a resolution of about 100 x 200 
hints anyone?

---

### Post by nano_unanue on 2008-04-11
I am in the same case. My wacom table graphire works in Gutsy Gibbons, I made a clean install of Hardy Heron, and now only the pen is working! I reinstalled wacom-tools and the xorg-wacom-.... packages several times and the xorg.conf wasn't touched!

Here is my xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```



When i tried to make the same steps of adding 
```

   InputDevice    “cursor” “SendCoreEvents”
    InputDevice    “stylus” “SendCoreEvents”
    InputDevice    “eraser” “SendCoreEvents”

```


to the xorg.conf file section ```
ServelLayout
``` and the other stuff around:

```

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "Mode" "relative"
    Option         "USB" "on"
EndSection
Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "Mode" "absolute"
    Option         "USB" "on"
    Option         "PressCurve" "50,0,100,50"
EndSection
Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "Mode" "absolute"
    Option         "USB" "on"
EndSection

```


My Xorg collapsed! It only could work in a low, low resolution mode and the system freezes in the logout... So what can i do now? Do I should report this as a bug?


Thanks in advance

---

### Post by eel on 2008-04-11
relax, all is not lost!
press ctrl-alt-F1 to reboot in terminal
you can just login as usual it just looks a bit less shiny 
(just your computer name and a : )

write down the following code and  type it as soon as you get to the 
yourname~$

```
sudo dpkg-reconfigure -phigh xserver-xorg
```


If any part of this message is unclear to you don't hesitate to ask again!

---

### Post by Nanounanue on 2008-04-11
Thank's for your help, but the wacom problem prevails. ...

I already report a bug:

[https://bugs.launchpad.net/ubuntu/+bug/215689](https://bugs.launchpad.net/ubuntu/+bug/215689)


But thanks again!

---

### Post by eel on 2008-04-12
read [this]("http://ubuntuforums.org/showthread.php?p=4701832&posted=1#post4701832") thread, it has a happy ending!!!

---

### Post by Nanounanue on 2008-04-13
thanks!!!

It worked flawless!

Let me check if the eraser and the pressure work as should!


Thanks again

---

### Post by Nanounanue on 2008-04-13
Eraser is not working either in Gimp or in Inkscape or Xournal... 

What could i do?


By the way pressure is working ok!


Adolfo

---

### Post by eel on 2008-04-13
My eraser isn't working now, but it didnt work in gutsy either and i never got around to fixing that so i have no ideas about that

---

### Post by P_Badger on 2008-04-13
I still had to add a bunch of stuff to my xorg.conf file before I could get my wacom graphire3 working properly, otherwise it would just behave like a normal mouse.

I get the feeling that tablet users are too small a niche for developers to worry too much about. Not to trash the folks working on the wacom linux drivers, without them, we'd be SOL.

Here's the wacom section from my xorg file, it's what has always worked on my system.

```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option        "USB"           "on"
        Option "PressCurve" "50,0,100,50" 
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option        "USB"           "on"  
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option        "Mode"          "relative"
        Option        "USB"           "on"  
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
        screen "Default Screen"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"
EndSection

```

---

### Post by ryansinn on 2008-04-14
My ThinkPad X61T does not work out of the box with Hardy either.

I will see if there are any bugs registered against this issue

This might provide a fix for you
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/215689](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/215689)

---

### Post by homburg on 2008-04-30
I used my Graphire 3 usb with a nvidia twinview setup og a desktop computer a while ago (Gutsy or earlier).

I think I had to tweak xorg.conf to get the correct behavior: absolute etc.

The linux driver was able to switch screen when I approached the middle edge of either screen...an innovation the windows driver hasn't implemented as of version 5 of their driver. On windows I had to choose between using it only on one screen or with a bad aspect ratio on both screens simultaniously.

That's the kind of hardware support that makes Ubuntu a huge step forward compared to a certain OS from 2001 :-)

Nothing useful here, just a story with a happy ending :-)

---

