---
title: "Dapper and Synaptics Touchpad"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-20
I am using Dapper on my laptop.

My touchpad is working, I can move the mouse and open folders, the buttons work too.

But the scrolling doesn't work, and there does not appear to be any entry for the touchpad in xorg.conf

Does this mean the touchpad is not configured and is simply functioning as a mouse?

How do I configure the touchpad in Dapper? I have seen gsynaptics mentioned, but I can't find it in the package manager, perhaps its not available for Dapper?

---

### Post by nickpaton on 2006-11-20
Found this link to gsynaptics, which by its date does seem to indicate that it is available as a .deb for Dapper:

[https://sourceforge.jp/projects/gsynaptics/]("https://sourceforge.jp/projects/gsynaptics/")

---

### Post by Zeerak on 2006-11-20
My xorg.conf looks like this (running edgy)
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
```

The only difference (I can see without a problem) is the ZAxisMapping, in Dapper it's "4 5" instead of "6 7"

---

### Post by PartisanEntity on 2006-11-20
Thanks to the both of you:

@nickpaton: this deb file is not in japanese is it? :)

@Zeerak: My mouse works, its the touchpad I am talking about.

---

### Post by nickpaton on 2006-11-20
> **PartisanEntity said:**
> Thanks to the both of you:

@nickpaton: this deb file is not in japanese is it? :)

Konichiwa! Bonjour! Al salaam a'alaykum! Ni hao! Hello! ¡Hola! Chào! Bon giorno! Guten Tag! Jambo! Zdravstvuite! Shalom! Dobar Dan!

Good question - don't actually know - just did a search and found it.  What would a Japanese Touchpad actually do?!

Seriously my touchpad was detected in both Dapper and Edgy and I only put on the Edgy package "coz it was there".

I would say in regard to my suggestion, use with caution PartisanEntitiy

---

### Post by PartisanEntity on 2006-11-24
I have installed the driver for the touchpad from the link mentioned above.  Now I have a Touchpad option in System > Preferences, but when I click on it, it can't initialise and tells me that SHMConfig should be set to 'true' in xorg.conf.

 I searched xorg.conf but there is no SHMConfig in it. 

** I can't even find any entries for a touchpad in xorg.conf  **

Anyone know what I can do now?  I did find a wacom stylus entry even though i dont have such hardware, could it be that Dapper thinks my touchpad is a wacom styluse board?  

Have a look yourselves:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection
``````
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
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
```

---

### Post by justinc on 2006-11-24
I got all the features of my synaptics touchpad working, on my laptop with Edgy, with this [config file](http://librarian.launchpad.net/1821293/xorg.conf) I found on [launchpad](https://launchpad.net/distros/ubuntu/+source/xorg-driver-synaptics/+bug/36219).


```
Section "InputDevice"
        Identifier      "ALPS"
        Driver          "synaptics"
	Option		"CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	Option		"LeftEdge"              "120"
	Option		"RightEdge"             "830"
	Option		"TopEdge"               "120"
	Option		"BottomEdge"            "650"
	Option		"FingerLow"             "14"
	Option		"FingerHigh"            "15"
	Option		"MaxTapTime"            "180"
	Option		"MaxTapMove"            "110"
	Option		"ClickTime"		"0"
	Option		"EmulateMidButtonTime"  "75"
	Option		"VertScrollDelta"       "10"
	Option		"HorizScrollDelta"      "10"
	Option		"MinSpeed"              "0.45"
	Option		"MaxSpeed"              "0.75"
	Option		"AccelFactor"           "0.020"
	Option		"EdgeMotionMinSpeed"    "200"
	Option		"EdgeMotionMaxSpeed"    "200"
	Option		"UpDownScrolling"       "1"
	Option		"CircularScrolling"     "0"
	Option		"CircScrollDelta"       "0.1"
	Option		"CircScrollTrigger"     "2"
	Option		"SHMConfig"		"true"
EndSection
```

I had to change the Identifier section from "ALPS" to "Synaptics Touchpad" I also added 'Option "SendCoreEvents" "True"' because it was under my original Synaptic's section.

I'm not sure what all of the options do, or if I/you need them all but I now have vertical and horizontal scrolling that works.

---

### Post by bodycoach2 on 2006-11-24
I use qsynaptics touchpad controller. It's in the Synaptic (apt-get) respostories. You might need universe and multiverse enabled.

It fixes the scrolling issue, and the 'tapping'. I can't stand the tapping for mouse selection, as it tends to move if my palm just lightly touches it. I can disable tapping in qsynaptics.

When I did a search, I noticed there was a ksynaptics too. 

Has anyone tried all these different drivers?

> **nickpaton said:**
> Found this link to gsynaptics, which by its date does seem to indicate that it is available as a .deb for Dapper:

[https://sourceforge.jp/projects/gsynaptics/]("https://sourceforge.jp/projects/gsynaptics/")

---

### Post by PartisanEntity on 2006-11-24
I installed qsynaptics using Synaptics Package Manager.

Now when I try to run qsynatpcics it tells me I need to install the synaptics driver.

Synaptics Package Manager informed me that ubuntu-desktop would have to be removed if I wanted to install qsynaptics.

What does this mean and how would it affect me?

Thanks.

screenshot attached.

---

### Post by nickpaton on 2006-11-24
@PartisanEntry.

Mmmm just read your last post.  Not sure if it's a good idea to continue, since I don't know what it's getting at if it's going to remove ubuntu-desktop.  You're on your own on this one I'm afraid but if it goes wrong and you are willing to reinstall the distro, then give it a go!! LOL

However, looking at your xorg.conf file, you don't have the same touchpad file that I have (probably coz you have not yet installed) (also I have Edgy remember and you are Dapper), but for what it's worth, that section of xorg on my box looks like this:

```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "uk"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

[B]Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "true"
EndSection[/B]

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection
```

I've made it bold for emphasis. Suggesting back up existing xorg.conf file first before proceeding further.

Let me know how it goes.

---

### Post by PartisanEntity on 2006-11-24
@nickpaton

Tried it, when I try to launch the touchpad icon in System > Preferences I still get the error message about SHMConfig.

added screenshot

---

### Post by nickpaton on 2006-11-24
Yup I remember now I had the same thing, so addded the line in Xorg.conf file:

```
Option	    "SHMConfig" "true"
```

Find a suitable place to insert it.
Have a look at my previous post - you may not have the synaptics touchpad section but see if you can find a sensible place to put it.

---

### Post by PartisanEntity on 2006-11-24
Can I enter it by itself anywhere or does it need to be within a:

Section "Something"

...

EndSection

---

### Post by nickpaton on 2006-11-24
> **PartisanEntity said:**
> Can I enter it by itself anywhere or does it need to be within a:

Section "Something"

...

EndSection

Before answering, can you again post the relevant secion of Xorg.con, from Keyboard to the last Wacom.  
This is because you have installed the touchpad file and I want to see if there are any differences from the first one you posted.

---

### Post by PartisanEntity on 2006-11-24
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection
```

Here is the rest including the bit you asked me to try and insert to see if it works, highlighted in red.

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
EndSection

[COLOR="Red"]Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "true"
EndSection[/COLOR]

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

```

---

### Post by nickpaton on 2006-11-24
You have the order of the Sections different to mine.

Try changing to:

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
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

[COLOR="Red"]Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "true"
EndSection[/COLOR]

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
```

It may need a mouse Input device as the first one.

other than that, I'm clean out of ideas.

---

### Post by PartisanEntity on 2006-11-24
It worked! I also had to add the touchpad to the server layout section.

Now I can edit it with qsynaptics, nice :)

Thank you!

---

### Post by nickpaton on 2006-11-24
Itza pleasure and I've learnt something new too with the qsynaptics for 6.06.

---

### Post by axle_foley00 on 2006-11-29
Wow thanks guys. This worked for me too. :)

---

