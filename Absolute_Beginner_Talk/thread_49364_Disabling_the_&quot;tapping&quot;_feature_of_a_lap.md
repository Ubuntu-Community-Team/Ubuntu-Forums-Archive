---
title: "Disabling the &quot;tapping&quot; feature of a laptop touchpad..."
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by Saponification on 2005-07-16
I've just installed *ubuntu* on an Acer Extensa 2355XC. Right away, something's bugging me - it's that darn "tapping" feature the touchpad thinks is helpful. Maybe some people like it, but I don't.

I've had a quick look in the settings and can't find anything about it, so how do I kill it? I'm new to *Linux* so I'd prefer to be able to do it in the GUI. I don't know anything about the CLI yet. I haven't even had a chance to look at it.

On a side note, the sensitivity of the pad is also an issue. I turned both it and the acceleration right down but it's still pretty fast. Too fast for my taste. Is there any way I can turn it down even further?

---

### Post by dolphinsonar on 2006-12-11
I would like to know as well.

---

### Post by Falcorian on 2006-12-12
I too would be interested in turning this off if possible.

---

### Post by msak007 on 2006-12-12
There's an app in the repositories called [qsynaptics]("http://qsynaptics.sourceforge.net/"). It's a GUI front-end to control libsynaptics and configure a touchpad. Give it a shot and see if it helps you.

---

### Post by zekonology on 2006-12-12
me too want to know the answer how. Thanks

---

### Post by Kobalt on 2006-12-12
But does qsynaptics works with other touchpads than synaptics ones' ?

---

### Post by seijuro on 2006-12-12
look for this section in your xorg.conf

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```

add that last line "Option..SHMConfig..."

then run

```
synclient RTCornerButton=0 RBCornerButton=0 TapButton1=0 TapButton2=0 TapButton3=0

```

you can add this command to a script to and have it run each time X loads.

---

### Post by mandragor on 2007-01-14
That doesn't work at all, for me. This is insane, my xorg.conf uses every possible
option to turn off tapping, but still I can't get rid of it. This is the relevant parts of my
xorg.conf:

Section "InputDevice"
        Driver "synaptics"
        Identifier "ALPS"
        Option "AlwaysCore"
        Option "Device" "/dev/input/mouse1"
        Option "Protocol" "auto-dev"
        Option "MaxTapTime" "0"
        Option "MaxTapMove" "0"
        Option "MaxDoubleTapTime" "0"
        Option "TapButton1" "0"
        Option "TapButton2" "0"
        Option "TapButton3" "0"
        Option "ClickTime" "0"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta" "0"
        Option "HorizScrollDelta" "0"
        Option "UpDownScrolling" "0"
        Option "TouchpadOff" "2"
        Option "SHMConfig" "on"
EndSection

---

### Post by ianmac on 2007-01-19
> **mandragor said:**
> That doesn't work at all, for me. This is insane, my xorg.conf uses every possible
option to turn off tapping, but still I can't get rid of it. This is the relevant parts of my
xorg.conf:

Section "InputDevice"
        Driver "synaptics"
        Identifier "ALPS"
        Option "AlwaysCore"
        Option "Device" "/dev/input/mouse1"
        Option "Protocol" "auto-dev"
        Option "MaxTapTime" "0"
        Option "MaxTapMove" "0"
        Option "MaxDoubleTapTime" "0"
        Option "TapButton1" "0"
        Option "TapButton2" "0"
        Option "TapButton3" "0"
        Option "ClickTime" "0"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta" "0"
        Option "HorizScrollDelta" "0"
        Option "UpDownScrolling" "0"
        Option "TouchpadOff" "2"
        Option "SHMConfig" "on"
EndSection

hmmm...  as far as I know (and I haven't checked), most of the settings cannot be specified in the xorg.conf file.  Check your log file to see how x responded to them.  The important option is SHMConfig on.  If you have this set, then from the shell you can do a synclient -l (to list the settings) and a synclient maxtaptime=0 to turn off tapping.  If you install the qsynaptics client, then you can use it (it is a graphical interface so you don't have to use the shell) instead.

Ian

---

### Post by Rychek on 2007-01-23
Does the SHMConfig work in 64 bit Ubuntu?

---

### Post by Lord Of The Dance on 2007-01-28
EDIT: Ignore this, it did appear to work, but whenever I restarted X, tapping switched on again for some reason.


[COLOR="Silver"]I just figured out how to turn it off on my laptop. Originally I tried using qsynaptics, but Ubuntu was using generic drivers, so this is what I had to do to turn off tapping:

It might be a good idea to backup /etc/X11/xorg.conf before starting
>  sudo gedit /etc/X11/xorg.conf  

Find
> Section "ServerLayout"
[INDENT]	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
**        InputDevice    "Configured Mouse"**
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"[/INDENT]
EndSection

then replace > InputDevice    "Configured Mouse" with > InputDevice    "Synaptics Touchpad"

Now Find
> Section "InputDevice"
[INDENT]       Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"[/INDENT]
EndSection

And replace the whole thing with
> Section "InputDevice"
[INDENT]        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"[/INDENT]
EndSection

Now install the qsynaptics frontend:
> sudo apt-get install qsynaptics
sudo qsynaptics

From the frontend it should be easy to disable tapping.[/COLOR]

---

### Post by moshuptrail on 2007-01-28
There is a nice HowTo on this topic.  Note the first solution is not the only one that works:
[http://www.ubuntuforums.org/showthread.php?t=271052&highlight=synaptics](http://www.ubuntuforums.org/showthread.php?t=271052&highlight=synaptics)

---

### Post by wpshooter on 2007-01-28
Someone that has this problem should consider reporting it as a bug.

I would think that if the hardware detection was doing the proper job, that this would be done automatically during the installation of Ubuntu and not be left up to the user to have to figure out.

---

### Post by jmpmjmpm on 2007-02-01
> **Lord Of The Dance said:**
> I just figured out how to turn it off on my laptop. Originally I tried using qsynaptics, but Ubuntu was using generic drivers, so this is what I had to do to turn off tapping:

It might be a good idea to backup /etc/X11/xorg.conf before starting


Find


then replace  with 

Now Find


And replace the whole thing with


Now install the qsynaptics frontend:


From the frontend it should be easy to disable tapping.

There is no need to relpace the above lines, simply add the new synaptic ones, it does the same thing.

---

### Post by ataranea on 2007-02-13
where do i go to access the xorg.conf  ????

---

### Post by ataranea on 2007-02-13
nvm figured it out.

---

