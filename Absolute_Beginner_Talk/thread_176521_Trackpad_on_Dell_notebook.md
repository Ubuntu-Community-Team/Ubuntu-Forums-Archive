---
title: "Trackpad on Dell notebook"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by DavidFourer on 2006-05-14
This might serve as a caution to someone thinking of installing Linux for the first time.  Read on.

Trackpad efforts  (poorly adjusted tap feature, want to dissable tap=click)

I'm working in my first ubuntu install and my first linux install.
Late-model Dell Inspiron 6000 notebook computer, Ubuntu 5.10

After reading a lot of detailed info on trackpads on the forums, I left some replies, but as they were long, old threads, I didn't get responses.  I've decided to try assembling a coherent and brief description here.

Perhaps someone will offer some explanation of what is going on, in addition to a fix.

The following suggested file has trackpad information but too much detail:
/usr/share/doc/xorg-driver-synaptics/README.gz

There is a text file called /proc/bus/input/devices:
N: Name="AT Translated Set 2 keyboard"<snip>
N: Name="PC Speaker"<snip>

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse0 event1 ts0 
B: EV=7 
B: KEY=70000 0 0 0 0 0 0 0 0 
B: REL=3 

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1 
B: EV=f 
B: KEY=420 0 70000 0 0 0 0 0 0 0 0 
B: REL=3 
B: ABS=1000003 

Suggested implication: system identifies my trackpad as "AlpsPS/2 ALPS GlidePoint"

A text file called /etc/x11/xorg.config contains perameters including several "InputDevice" sections of perameters:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection
		<snip>
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

The following "ALPS" section was suggested as perameters by another user:

Section "InputDevice"
Identifier "ALPS"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/input/event5"
Option "Protocol" "event"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "15"
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "true"
EndSection
		and a different "Mouse" section:
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

and the following changes from "Synaptics Touchpad" to "ALPS" in the section called "ServerLayout".

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "ALPS"
EndSection

I went ahead and made all the changes.  I also changed "MaxTapTime" and "MaxTapMove" to "0".  I tried leaving everything in the original way but adding the line -- Option "MaxTapTime" "0"

I rebooted after making changes.
None of this had any effect on my trackpad, which still clicks when I move the pointer.

It's very possible that I did something right but had a wrong case or missed quote or some syntax error.  Since I don't really know what I'm doing, I do a lot of unnecessary stuff and it's hard to try everything three times to be sure I got it right.  That's why it would be helpful to have an explanation of what's going on.

It might not look like it, but reading all this, thinking about it, and trying the changes, is a incredible amount of work for me.  Maybe 12 hours.  Maybe more.  

I actually did fix some things on this install.  I got suspend-to-ram to work in under 2 hours.  That's a pretty essential feature for me.  I've been getting my work done on this computer for a while.  The display looks as good as it did with Windows.  Browsing with Firefox is exactly the same.  Sometimes videos will play, sometimes not.  It's a normal computer.

I used to lament that I couldn't see what was going in Windows.  Now I can see it all and none of it is comprehensible.

In brief, it's not impossible.  Just improbable.

David

---

### Post by johnc4510 on 2006-05-14
David,
While I can't help you, I will commend you on your research and trying to learn something the old fashion way. I hope someone who knows what to do will help. Good luck and don't let it get you down, you'll get there

---

### Post by uzi09 on 2006-05-14
i had the exact same problem, heres what you do:
go to /etc/X11/xorg.conf
make a backup
then find this part:

```

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

```

change it to the following:

```

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "MaxTapTime"       "0"
EndSection

```

then restart gnome (or just reboot the computer if that is too difficult)


> 
I left some replies, but as they were long, old threads, I didn't get responses.

is Ubuntu support the greatest or what? ;)

---

### Post by DSn0wMan on 2006-05-14
Same problem here with Dell Inspiron 600. touchpad=way too sensitive

I also tried setting the MaxTapTime to 0. No dice. 

Luckily I use a USB mouse, and have adapted not touching the thing accidentally while typing.

It would be nice to get it working right though.

---

### Post by uzi09 on 2006-05-14
[QUOTE=DSn0wMan]Same problem here with Dell Inspiron 600. touchpad=way too sensitive

I also tried setting the MaxTapTime to 0. No dice. 

Luckily I use a USB mouse, and have adapted not touching the thing accidentally while typing.

It would be nice to get it working right though.[/QUOTE]

Sorry, I'm not sure what you mean. MaxTapTime is used to disable the "tap-to-click" feature -- not sensitivity.

for sensitivity, go to the mouse options (sorry, not sure what version of Ubuntu you're using, but command line always come through 8)):
type in a terminal:
```

gnome-mouse-properties

```

go to the motion tab and change sensitivity there.

lemme know if it worked

---

### Post by DSn0wMan on 2006-05-14
[QUOTE=uzi09]Sorry, I'm not sure what you mean. MaxTapTime is used to disable the "tap-to-click" feature -- not sensitivity.

for sensitivity, go to the mouse options (sorry, not sure what version of Ubuntu you're using, but command line always come through 8)):
type in a terminal:
```

gnome-mouse-properties

```

go to the motion tab and change sensitivity there.

lemme know if it worked[/QUOTE]

Its so sensitve that when I get close to it, it fires off a click event. Sorry if I was not clear.

edit: so I just want to disable the clicking of the touchpad.

---

### Post by DavidFourer on 2006-05-14
[QUOTE=DSn0wMan]Its so sensitve that when I get close to it, it fires off a click event. Sorry if I was not clear.
edit: so I just want to disable the clicking of the touchpad.[/QUOTE]

That's the problem I have.  I like that comand like trick though -- "gnome-mouse-properties".  I think in that window, setting sensitivity to max makes the mouse movement smoother for some reason.

---

### Post by uzi09 on 2006-05-14
ic, and the MaxTapTime didn't work right? hmmm, let me look into this and double check if that is what its called.

edit: sorry, that seems to be the command. one thing i forgot to mention though is that you probably need to restart gnome (just reboot the computer and it should do the trick).

let me know what you come up with

---

### Post by uzi09 on 2006-05-15
*bump*

sorry for double posting, but i guess i edited the last post and i thought maybe you guys didn't bother checking because it didn't say a new post was added :\

if any mods want, feel free to remove this...thanks (and sorry again)

i'm curious to see if it worked out for you

---

### Post by DSn0wMan on 2006-05-15
[QUOTE=uzi09]
 you probably need to restart gnome (just reboot the computer and it should do the trick).
[/QUOTE]

I tried the setting, and restarting, and that didn't clear it up. I am gussing that MaxTapTime is the wrong parameter. Befor I edit /etc/X11/xorg.conf The synaptics touchpad section doesn't have a MaxTapTime parameter.

It seems to me that MaxTapTime would have to map to a double click event.

I would rather get rid of the click event all together, since there are 2 buttons below the pad that work fine for clicking, and it's pretty difficult to click those accidentally.

---

### Post by uzi09 on 2006-05-16
heres the (trimmed) output of my /etc/X11/xorg.conf file:
```

        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "MaxTapTime"            "0"
EndSection

```

idk, it works for me -- that's really odd. umm btw, what version of ubuntu are u using? i'm using dapper...

---

### Post by DSn0wMan on 2006-05-16
I am on breezy. I guess I'll just deal with it, or maybe just disable the whole thing.

It's not really a big deal!

I appreciate the help. Thanks

---

### Post by DavidFourer on 2006-05-16
I've double checked everything and it doesn't work on breezy but people with dapper are doing fine.  That seems to be the catch.  So something was changed in breezy and we don't know what that was.  

Can someone explain why we are running two versions?  When did these versions come out?  What is the significance?  Will there be a newer version and will I be able to upgrade?  

(Gee this guy has a lot of questions.  Who invited him on here?)

---

### Post by Sef on 2006-05-16
> (Gee this guy has a lot of questions. Who invited him on here?)

We love questions here, so he should keep asking.  

> Can someone explain why we are running two versions? When did these versions come out? What is the significance? Will there be a newer version and will I be able to upgrade?

Breezy is the current stable version.  Dapper is the update version.  It is in Beta now. It will become the new stable version on 1 June.  Yes you will be able to upgrade.

---

### Post by DavidFourer on 2006-05-16
Sef wrote:
> Breezy is the current stable version. Dapper is the update version. It is in Beta now. It will become the new stable version on 1 June. Yes you will be able to upgrade.
That solves the problem with the trackpad.  Since the fix in this and other threads has worked in Dapper, I only have to wait till June 1 and "upgrade".  Thank you for that simple answer.

I see Sef wrote from Korea.  I will try to get my location into my profile on this forum.  It's Chicago, USA

---

### Post by DavidFourer on 2006-05-16
Here's an interesting option.  A GUI for adjusting synaptic-driver trackpad.
[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)
The instructions for installation are a little complex but I might make a project out of that.

---

### Post by uzi09 on 2006-05-17
if you'd like, u're more than welcome to switch to it now. i've been using dapper since march and for the most part it works perfectly fine. the only thing is there are major updates on pretty much a daily basis and sometimes an update may stop something from working, but it'll be fixed (probably better than before) on the next update.

so far it hasn't been that big of a problem, and considering how it's May 17th today anyway - June 1st isn't too far off.

enjoy,
uzi

---

