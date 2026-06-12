---
title: "Touchpad sensitivity/accuracy is really bad?"
date: 2007-11-10
forum: Apple Intel Users
---

### Post by jasonparekh on 2007-11-10
Running Gutsy on MBP rev3.  Using appletouch + synaptics, I've noticed the the pointer isn't smooth at all.  What I mean:  move the mouse diagonally from upper-right to lower-left and the pointer looks 'drunk' by going left-down-left-down-left-...  Do you guys see this also, or could it be something on my end?

If you guys see this also, I'll look into appletouch to find the problem.

Thanks,
jason

---

### Post by God of the Meeps on 2007-11-10
Maybe the problem is that you have too high/low sensitivity or speed?

---

### Post by ChardFi on 2007-11-11
I hear ya,
Add these lines
```
Option         "AccelFactor" "0.2"
Option         "MinSpeed" "0.4"
Option         "MaxSpeed" "1.5"
Option         "FingerLow" "5"
Option         "FingerHigh" "25"
```

```
Option "TapButton2" "3"
Option "TapButton3" "2"
```

to the 
Section "InputDevice"
Identifier "Synaptics Touchpad" 
Of your xorg.conf 

Works a treat!

---

### Post by cleentrax on 2007-11-11
On my Santa Rosa MB (2.2ghz) the xorg.conf settings don't make any difference. I think the new touch pads don't work with the linux synaptics driver. We may need to wait for a new kernel.

---

### Post by jfrorie on 2007-11-12
> **cleentrax said:**
> On my Santa Rosa MB (2.2ghz) the xorg.conf settings don't make any difference. I think the new touch pads don't work with the linux synaptics driver. We may need to wait for a new kernel.

From my reading, changes to the synaptics area of xorg.conf are ignored if you have the gsynaptics running.  Check System->Prefs->Sessions to see if this is the case.

I've made my touchpad work much better by playing with the gsynpatics parameters.

---

### Post by cleentrax on 2007-11-13
> **jfrorie said:**
> From my reading, changes to the synaptics area of xorg.conf are ignored if you have the gsynaptics running.  Check System->Prefs->Sessions to see if this is the case.

I've made my touchpad work much better by playing with the gsynpatics parameters.

Gsynaptics won't even run on my rev3 macbook. It says there is no synaptics device.

---

### Post by jfrorie on 2007-11-13
> **cleentrax said:**
> Gsynaptics won't even run on my rev3 macbook. It says there is no synaptics device.

Sorry.  I should have explained a little better.  I believe that the touchpad control software gsynaptic and probably appletouch will override xorg.conf.  If you make changes to the file, they may be ignored.  That's what I have read.

Twitchy mouse operation was resolved for me by reducing sensitivity in the motion and reducing the speed of the tap (if you have that enabled).  It's not perfect, but MUCH better.

---

### Post by cyberdork33 on 2007-11-13
appletouch is a kernel module not a xorg driver. 

There are patches to recognize the new hardware ID of the Touchpad on the newest Macbooks:
[http://ubuntuforums.org/showthread.php?t=610375](http://ubuntuforums.org/showthread.php?t=610375)

---

### Post by jfrorie on 2007-11-13
> **cyberdork33 said:**
> appletouch is a kernel module not a xorg driver. 



Oops.  My bad. :)

---

### Post by cyberdork33 on 2007-11-13
> **jfrorie said:**
> Oops.  My bad. :)

It still could be the issue though, as Synaptic may not detect the touchpad correctly because the appletouch module needs to be fixed.

---

### Post by Baerun on 2008-02-22
I'm on a macbook and I just got my touchpad working with synaptics well. 

I had to make a few changes to my /etc/X11/xorg.conf however.

To the Section "ServerLayout":
```
InputDevice    "Synaptics"  "SendCoreEvents"
```

```
Section "InputDevice"
	Identifier "Synaptics"
	Driver "synaptics"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "auto-dev"
	Option "Emulate3Buttons" "yes"
	Option "SHMConfig" "on"
	Option "AccelFactor" "0.2"
	Option "MinSpeed" "0.4"
	Option "MaxSpeed" "0.5"
	Option "FingerLow" "5"
	Option "FingerHigh" "25"
EndSection
```

I also had to add a modules section:
```
Section "Module"
	Load "synaptics"
EndSection
```

---

### Post by GalloGlas on 2008-02-23
> **ChardFi said:**
> I hear ya,
Add these lines
```
Option         "AccelFactor" "0.2"
Option         "MinSpeed" "0.4"
Option         "MaxSpeed" "1.5"
Option         "FingerLow" "5"
Option         "FingerHigh" "25"
```

```
Option "TapButton2" "3"
Option "TapButton3" "2"
```

to the 
Section "InputDevice"
Identifier "Synaptics Touchpad" 
Of your xorg.conf 

Works a treat!

Every time I do this it causes Linux to not startup.  Then I have to pop in the Live CD, go onto the disk, and change the xorg.conf file back to its original state.  Once I do that, ubuntu starts up good.

---

### Post by cyberdork33 on 2008-02-23
> **GalloGlas said:**
> Every time I do this it causes Linux to not startup.  Then I have to pop in the Live CD, go onto the disk, and change the xorg.conf file back to its original state.  Once I do that, ubuntu starts up good.

I'd like to make a slight distinction. Linux is starting fine, it is xorg that is not starting. I do not know why those changes would prevent xorg from starting. what happens in the end? Is it just a black screen with nothing? Is there any error messages?

---

