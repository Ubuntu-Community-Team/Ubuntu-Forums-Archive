---
title: "Multi button mouse"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jasonsfakename on 2006-09-19
I have a logitech Mx revolution mouse and was wondering if there was any way to utilize it in ubuntu/firefox. I enjoy the extra control it gives me in windows and would like the same for ubuntu. Mainly the back and forward feature.

this is my mouse
[http://www.logitech.com/index.cfm/products/upp/details/US/EN,crid=2676,contentid=12134&ad=revolution_mxupp]("http://www.logitech.com/index.cfm/products/upp/details/US/EN,crid=2676,contentid=12134&ad=revolution_mxupp")
Keep in mind that I am a noob here. Thanks

---

### Post by p388l3s on 2006-09-19
There is a guide on these very forums for that exact mouse although to get it working in firefox you can do the following:

in a terminal type

```
sudo gedit /etc/X11/xorg.conf
```

once you have the gedit window open you need to look for the section for your mouse here's mine:

```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	[B]Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"[/B]
EndSection
```

the piece you need for your mouse are highlighted, this enables the 2 side buttons, if you have emulate 3 button mouse enabled then you can just comment it out with a # at the beginning.

once i find that guide i'll post the link here.

and here it is

[http://www.ubuntuforums.org/showthread.php?t=219894](http://www.ubuntuforums.org/showthread.php?t=219894)

Good luck.

Pebbles.

---

### Post by jasonsfakename on 2006-09-20
Thanks

---

### Post by Drakkor on 2006-09-20
I tried that awhile back and found it rather difficult.
Firefox has an extension called "Mouse Gestures" and now
I just left-click drag left to go back and left-click drag right to go forward,it works for me ! :p

---

### Post by DianeOfTheMoon on 2006-09-23
I've been trying to follow that guide, and while it works to some degree, I can't seem to get to get xev to show events for the wheel left/right and for the thumb rocker...has anyone gotten these to work?

---

### Post by Victor Quezada on 2006-09-30
I just got an MX revolution too, but i cannot get it going, could any of you tell me step by step instructions how to make it work? keep in mind i am getting introduced to the ubuntu plataform. thanks

---

