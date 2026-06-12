---
title: "Dell D820 Latitude - UBUNTU 7.10 - Touchpad not working at all!!"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by pdaalder on 2008-01-25
Hi

I'm trying to get the touchpad to work, but as far as I can figure out the ubuntu system doesn't even regonises the device.

The trackball (the red stick in the keyboard) works find, the buttons work find (all 4).

below the output of: sudo synclient -h
Hardware properties:
    Can't detect hardware properties.
    This is normal if you are running linux kernel 2.6.
    Check the kernel log for touchpad hardware information.
Driver version: 1406

I've tried  in xorg.conf:
- the load option
- modifying "	Identifier	"Synaptics Touchpad"" with all flavors I've seen (Some making xserver to stop working properly)

As I'm still learning ubuntu, I'm not yet sure what nxt step is.

Just a preview of outstanding problems I have beside this:
- getting my 7-button mouse to work (non of the help/forum info so far worked, tried xev, but this doesn't regonizes button 6,7)
- getting my soundcard to produce some level of quality sound
- getting voip software to work (in/output audio don't work)
- regular network card to accepted plugged in Ethernet cable.
- learning ubuntu :-)

I hope somebody came across similar problems, and has some good tips on how to proceed

Cheers for the reply

(And I've been googling for the last 6 days till 1h00 to figure out what can fix my problems, probably searching the incorrect terms :-( )

---

### Post by pdaalder on 2008-01-28
hi, pls anyone. 

I've found out that my touchpad is an ALPS. Still don't have the 7 mouse buttons working, nor the touchpad. Going to investigate soundcard for the next 5 days ;-).

Life shouldn't be this hard!!!

Peter

---

### Post by pdaalder on 2008-02-11
To provide some update:

#sudo killall mouseemu

This command solved many of my problems regarding mouse:
- touchpad - FIX
- Mouse freezing while using keyboard - FIX
- 7-buttons - Investigating

---

### Post by pdaalder on 2008-02-11
oeps, found this in:
[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344)

---

### Post by LowSky on 2008-02-11
here is how to get all the buttons working on your mouse

in terminal type 

```
sudo gedit /etc/X11/xorg.conf
``` make sure X11 is capital X

then edit the mouse portion to this

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

---

