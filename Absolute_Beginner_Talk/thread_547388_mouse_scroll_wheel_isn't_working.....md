---
title: "mouse scroll wheel isn't working...."
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-09-10
well, I have never gotten my scroll wheel to work and this is an extremely simple mouse.
My X is working and I don't really want to go back through that again.

What do I need to do to get this scrolling feature to work?

---

### Post by jzonne on 2007-09-10
You can try the following: 
Typically to get scrolling, you add the line:
Code:

Option "ZAxisMapping" "4 5"

...to your /etc/X11/xorg.conf file under the section about your "pointer" or mouse. The section will look something, but not exactly like this:
Code:

# Option "ChordMiddle" Identifier "Mouse1" Driver "mouse" Option "Buttons" "5" Option "ZAxisMapping" "4 5" Option "Protocol" "IMPS/2"

To open your xorg.conf, open a terminal and type:
Code:

sudo gedit /etc/X11/xorg.conf

Look for the mouse section and edit accordingly. After editing, save and exit. You must restart xwindows before the change will take effect. Just reboot to do this.

Which i found here: [http://www.linuxforums.org/forum/ubuntu-help/75249-help-how-enable-scroll-wheel-my-mouse.html](http://www.linuxforums.org/forum/ubuntu-help/75249-help-how-enable-scroll-wheel-my-mouse.html)

---

### Post by chaddiesel on 2007-09-10
Well, I checked that and it actually has that in the mouse section.

Any other ideas?

---

### Post by chaddiesel on 2007-09-18
i've been working on this one for the week and haven't had any luck since. Here is what is says in the X server file.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"PS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

This is a five button dynex mouse, Three buttons work on it. The scroll wheel is not included in these three, some other side button works as a right click.

---

### Post by Daveth on 2007-09-18
a couple of ideas.

contact Phalangees who has the same mouse as you and ask what his/her settings are.

If this is a USB mouse (?) have you tried an aleternative Protocol setting in the Xorg.conf..

like "ExplorerPS/2"

from [http://ubuntuforums.org/showthread.php?t=224244&page=2](http://ubuntuforums.org/showthread.php?t=224244&page=2)

Just a thought.

---

### Post by qpieus on 2007-09-18
I agree with Daveth. I use  "ExplorerPS/2" and the scroll wheel works fine. Here's a portion of my xorg.conf:

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

---

### Post by lightstream on 2007-09-19
For the mouse protocol, there's also ImPS/2. I use ExplorerPS/2 as well, but it's an MS Explorer mouse. (MS hardware is the opposite of their software: well built and good value!)

As for the buttons thing, my mouse is 5 button, and I added the 'Buttons' and "ButtonMapping" settings to get those recognised (otherwise they do just duplicate functionality of buttons 2 & 3, ie right click & middle click). Note that the mouse is viewed as 7-button: the two numbers you have as 'Z-Axis Mapping' equate to mouse wheel up and mouse wheel down, and should not appear in the "ButtonMapping" setting.

Here's my xorg.conf:

```
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "Resolution"            "100"

```

My scroll wheel was working fine, I downloaded some updates yesterday, and when I switched it back on the wheel no longer worked. Still not found the fix ....

EDIT: Hardware problem. My scroll wheel was broken, must've been when the cat knocked it off onto the floor, gah! Wrong kind of mouse you daft cat!

---

