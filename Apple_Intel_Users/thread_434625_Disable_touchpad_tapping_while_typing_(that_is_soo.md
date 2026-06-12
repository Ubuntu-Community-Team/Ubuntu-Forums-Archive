---
title: "Disable touchpad tapping while typing (that is sooo annoying)"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by benanzo on 2007-05-06
I got ahold of a little insider secret for those of you who are exercising the advanced functionality of your touchpads on the MacBooks and Pros.

You need to have SHMConfig "on" in your xorg.conf in order for this to work.


You're going to use a little utility called syndaemon

make this script and have it run at login:

```

#!/bin/bash

# Disable touchpad for 2 seconds after last key press
# to prevent accidental touchpad activation while typing.

/usr/bin/syndaemon -d -t -i 2

```

the -d flag tells syndaemon to run all the time and monitor the keyboard presses
the -t flag tells it to only disable tapping and scrolling, not pointer movement
the -i flag is how long (in seconds) to disable the touchpad *after* the last keypress

There are a few other options available to fine-tune which keypresses count, ie Fn combos etc.

```
man syndaemon
```
will fill you in.

I felt this was just important enough to bring up 'cause, dang, I HATE it when my mouse jumps all over because I accidentally tapped the touchpad with my wrist.

---

### Post by edmondt on 2007-05-09
Nice tip! There is another thread about this...

[HowTo: Disable Synaptics Touchpad While Typing]("http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing") 

For more reading....

---

### Post by levmyshkin on 2007-05-17
I'm painfully new to Linux, but have years of intermediate level experience on computers. Decided to jump in feet first, get rid of Mac OSX, and learn by immersion. I'm running Feisty Fawn on a MacBook, and the touchpad sensitivity is driving me nuts.

I have a basic knowledge when it comes to working in Terminal, but I have no idea how to turn xorg.conf on.

Any suggestions? Once I figure out where how to turn on xorg.conf, I can execute the rest of that configuration posted. I'm up against a hell of a learning curve, so sorry if the question seems basic to the point of portraying me as idiotic.

(Nevermind. Please disregard this, I'll leave it for posterity but followed the link in the post right above this. Step one is all about how to turn on SHMconfig. Doh. Thanks for the great info and help you guys provide.)

Thanks from a newbie,

Lev

---

### Post by ronocdh on 2007-05-17
> **levmyshkin said:**
> I'm painfully new to Linux, but have years of intermediate level experience on computers. Decided to jump in feet first, get rid of Mac OSX, and learn by immersion. I'm running Feisty Fawn on a MacBook, and the touchpad sensitivity is driving me nuts.

I have a basic knowledge when it comes to working in Terminal, but I have no idea how to turn xorg.conf on.

Any suggestions? Once I figure out where how to turn on xorg.conf, I can execute the rest of that configuration posted. I'm up against a hell of a learning curve, so sorry if the question seems basic to the point of portraying me as idiotic.

(Nevermind. Please disregard this, I'll leave it for posterity but followed the link in the post right above this. Step one is all about how to turn on SHMconfig. Doh. Thanks for the great info and help you guys provide.)

Thanks from a newbie,

Lev
What Benanzo was referring to was editing a very common file used to store configuration settings for X. To edit this file, type in the terminal:
```
sudo gedit /etc/X11/xorg.conf
```
Then, once the text of the file is visible, you can add the Option Benanzo gives under the appropriate section (in this case, it'd be the section regarding your trackpad) with the value he gives (here, "on").

---

### Post by scottvan on 2007-05-21
> **levmyshkin said:**
> I'm painfully new to Linux, but have years of intermediate level experience on computers. Decided to jump in feet first, get rid of Mac OSX, and learn by immersion. I'm running Feisty Fawn on a MacBook, and the touchpad sensitivity is driving me nuts.

I have a basic knowledge when it comes to working in Terminal, but I have no idea how to turn xorg.conf on.

Any suggestions? Once I figure out where how to turn on xorg.conf, I can execute the rest of that configuration posted. I'm up against a hell of a learning curve, so sorry if the question seems basic to the point of portraying me as idiotic.

(Nevermind. Please disregard this, I'll leave it for posterity but followed the link in the post right above this. Step one is all about how to turn on SHMconfig. Doh. Thanks for the great info and help you guys provide.)

Thanks from a newbie,

Lev

How do you turn on SHMconfig?

---

### Post by ronocdh on 2007-05-21
> **scottvan said:**
> How do you turn on SHMconfig?
In the terminal, type: ```
sudo gedit /etc/X11/xorg.conf
```Then scroll to the section which pertains to your trackpad. Add the following line:
```
Option    "SHMConfig"         "true"
```

---

### Post by benanzo on 2007-05-21
Here is the touchpad section in my /etc/X11/xorg.conf

```

Section "InputDevice"
	Identifier	"MacBook Touchpad"
	Driver		"synaptics"
	Option 		"SHMConfig" "on"
	Option		"CorePointer"
	Option		"SendCoreEvents" "true"
	Option		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"LeftEdge" "100"
	Option 		"RightEdge" "1120"
	Option 		"TopEdge" "50"
	Option 		"BottomEdge" "310"
	Option 		"FingerLow" "20"
	Option 		"FingerHigh" "30"
	Option 		"MaxTapTime" "150"
	Option 		"MaxTapMove" "220"
	Option 		"MaxDoubleTapTime" "180"
	Option 		"VertScrollDelta" "25"
	Option 		"VertTwoFingerScroll" "true"
	Option 		"TapButton2" "3"
	Option 		"TapButton3" "2"
	Option 		"MinSpeed" "0.79"
	Option 		"MaxSpeed" "0.88"
	Option 		"AccelFactor" "0.015"
EndSection

```

---

### Post by Doc.Caliban on 2007-06-09
I'm using a Dell XPS2 notebook with a Synaptics touchpad yet this trick does not seem to work for me.  Does it only work on MacBooks?

My xorg.conf section:
```

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection

```

-Doc

---

### Post by ronocdh on 2007-06-09
> **Doc.Caliban said:**
> I'm using a Dell XPS2 notebook with a Synaptics touchpad yet this trick does not seem to work for me.  Does it only work on MacBooks?

-Doc
This forum is intended for users of Intel Macs, so the fixes discussed here pertain mostly that hardware. Of course, there are a few common tactics used (like installing the proprietary ATI driver) which a regular PC user would do, too, but for something like this, you're probably better off posting in a different forum.

---

