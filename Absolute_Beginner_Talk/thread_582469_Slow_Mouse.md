---
title: "Slow Mouse?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Vermishis on 2007-10-19
Hello! I Just installed Ubuntu for the first time! It's great! I love it! But, the mouse is really slow! is there anyway to change the speed. I'm using a Dell Inspiron 6000, and it's a touch pad.

P.S. I have the acceleration set as high as possible.

---

### Post by catfacts on 2007-10-21
Hmm... now on my computer the mouse prefs dont affect the touchpad at all, I can change anything and nothing happens.. this is odd... it may be a bug to report.

---

### Post by tuxsg on 2007-10-22
Me too, on XPS.

Should I edit something on Xorg conf files?

Thanks

---

### Post by teabeartom on 2007-10-22
> **tuxsg said:**
> Me too, on XPS.

Should I edit something on Xorg conf files?

Thanks

I had this problem too.  Then, one day while trying out the Mandriva Live CD, I noticed that my mouse was as fast as it used to be on Windows XP.  So, I copied the Mandriva mouse code into my xorg.conf file.  I had to change the device name and some other stuff, but now my xorg.conf looks like this (I included my old ubuntu settings commented out so you can compare -- If your settings look like my commented out one, then you can just copy and paste the new code... Be sure to delete or comment out your old "Synaptics Touchpad" code as I did.)

Before editing xorg.conf, make a backup by:

sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup.conf

Then, type in:

sudo gedit /etc/X11/xorg.conf

Here is my xorg.conf with a FAST Synaptics Touchpad

```

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option 		"SHMConfig" 		"true"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#EndSection

#New Synaptics from mandriva
Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    Option "EdgeMotionMinSpeed" "200"
    Option "MaxSpeed" "1.00"
    Option "MinSpeed" "0.8"
    Option "BottomEdge" "650"
    Option "SendCoreEvents" "true"
    Option "Protocol" "auto-dev"
    Option "Device" "/dev/psaux"
    Option "EdgeMotionMaxSpeed" "200"
    Option "CircScrollTrigger" "2"
    Option "UpDownScrolling" "0"
    Option "SHMConfig" "on"
    Option "LeftEdge" "120"
    Option "FingerLow" "14"
    Option "HorizScrollDelta" "20"
    Option "MaxTapMove" "110"
    Option "FingerHigh" "15"
    Option "VertScrollDelta" "20"
    Option "CircularScrolling" "1"
    Option "RightEdge" "830"
    Option "AccelFactor" "0.015"
    Option "TopEdge" "120"
EndSection

```

Note that I have a Dell Inspiron 6000, so it should work on yours too!  Any questions, just let me know.

---

