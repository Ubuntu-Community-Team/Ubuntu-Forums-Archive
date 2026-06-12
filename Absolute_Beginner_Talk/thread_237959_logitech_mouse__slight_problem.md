---
title: "logitech mouse  slight problem"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by w12gti on 2006-08-17
im really new to ubuntu(linux), been using it for about 1 week and i already love it... this is my first post by the way. 

got this annoying problem, whenever im playing quake 3, alienarena and warcraft III (those 3 are the only games currently installed) the mouse seems to freeze randomly for a few seconds throughout the game, i installed lomoco but it didnt solve the problem. sometimes the mouse freezes even if im not running anything, the mouse works perfect on my windoze pc, im gonna remove that windoze by the way when games with gameguard will run on ubuntu (i wish it would be sooner).

im using a p/s2 logitech mouse without the scroll.

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

---

### Post by wieman01 on 2006-08-17
Try again after removing these 2 lines (which you don't need if you haven't got a mouse-wheel):
> Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"

---

### Post by wieman01 on 2006-08-17
And another advice if everything else fails... Get yourself a new mouse before you waste too much time on it. Just a thought.

Some similar happened to me and kept me busy for a whole week! Then my keyboard (Logitech Cordless Duo) started to make trouble and I decided to have both keyboard & mouse replaced. I have not had a problem since.

---

### Post by w12gti on 2006-08-17
it didnt work, whats wrong with logitech mouse? 

anyway, what brand of mouse did you use? my logitech mouse served me well for around 3 years(gaming and other stuff), i wouldnt allow it to ruin my ubuntu experience so im gonna have to let it go.

thanks for your quick reply bud

---

### Post by wieman01 on 2006-08-17
I used to have the "Cordless MX Duo" with a MX700 wireless mouse. The mouse would behave erratically after a few minutes of usage and click around randomly without myself being able to figure out what the problem was. Others have reported the same issue & after my keyboard had stopped working I bought myself a new (wired) set (Logitech again). 

The wired set works perfectly. Is your mouse wireless?

As for the protocol, 2 more suggestions:
> Protocol "IMPS/2"
Or:
> Protocol "PS/2"
Do any of those options work?

---

### Post by w12gti on 2006-08-17
:D  

Protocol "PS/2"

this worked better, the mouse still freezes but i hardly notice it now, before it freezes like every 5 to 20 seconds (random).

my mouse is the ps/2 logitech M-s59a, its a wired mouse.

thanks wieman01 :KS

---

### Post by wieman01 on 2006-08-17
Most welcome. Perhaps it's really a hardware problem. Think about it and have fun! :-)

---

