---
title: "Macbook 1.1 jaunty issues"
date: 2009-04-25
forum: Apple Hardware Users
---

### Post by saarakura on 2009-04-25
i installed the 9.04 (jaunty) in my macbook 1.1 and it all went well...but brightness is bugging...before it goes out (brightness 0) the light keeps getting stronger as if brightness was set on max And  if i set sound on 0 it makes a noise. 

thanks for all!

---

### Post by genosupremo on 2009-04-25
I have a similar problem on my 2.1(jaunty): the brightness "scale" is simply totally random levels, from off to full-on, to a really worrying flickering, in no order. Several points in the scale correspond to off... 

Pretty annoying, especially the flickering. Could that damage my screen?..

---

### Post by Peasantoid on 2009-04-25
No problems here (3,1), although the slider is a little buggy &#8212; for one thing, setting it to 0 doesn't reduce it, but 1 does. (Feaure or bug? Hmm...)

About the flickering: I'm guessing yes, since it's basically turning the screen on and off again extremely quickly. That's going to age the hardware.

---

### Post by markitoxs on 2009-04-25
How does it work overall?

---

### Post by saarakura on 2009-04-25
on mine mac book 1.1 works great except for this 2 things.. the rest is OK desktop effects running right ....

---

### Post by genosupremo on 2009-04-26
> How does it work overall?
- Pretty nifty, but a bit buggy as a dualboot on my 2.1. Largest problem seems to be a general block in the update software: can't install/upgrade anything. Don't know my way around the system, can't rightclick... Hmm.

> About the flickering:
- What i figured. Ill look around, see if i find anything..

---

### Post by genosupremo on 2009-04-26
> Could that damage my screen?..
Answer is a solid yes, i (temporarily) lost the illumination behind a third of my screen. Dont know what to do about that, too dangerous to keep using linux? I expect my warranty mightn't be too happy about it, and its not predictable enough to avoid. 

Why internets, why?

---

### Post by Transistor23 on 2009-04-27
> **genosupremo said:**
> I have a similar problem on my 2.1(jaunty): the brightness "scale" is simply totally random levels, from off to full-on, to a really worrying flickering, in no order. Several points in the scale correspond to off... 

Pretty annoying, especially the flickering. Could that damage my screen?..

Same on my Macbook 2,1 with Jaunty. When I press the button that increases the brightness (or the button that decreases it), sometimes the screen brightness increases, sometimes it decreases, and other times it turns off. Anyone know how to fix this?

---

### Post by Transistor23 on 2009-04-27
Sorry for the double post, but I've found a bug on Launchpad about the brightness problem on the Macbook 2,1. Might be the same as the problem the OP (Macbook 1,1) is having also.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309)

---

### Post by saarakura on 2009-05-02
> **Transistor23 said:**
> Sorry for the double post, but I've found a bug on Launchpad about the brightness problem on the Macbook 2,1. Might be the same as the problem the OP (Macbook 1,1) is having also.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309)

Thanks this works :D,

Now about sound.. i open alsamixer and press key to down volume, and on alsamixer PCM reaches 0 but on key its only on half, and other thing whem i press key to mute its switch front to stereo / mono :confused:

---

### Post by slick666 on 2009-05-18
The link has been changed so here is the new link.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309")

What the fix is essentially the below xrandr command
```
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
```

fix worked for me

---

### Post by saarakura on 2009-05-21
> **slick666 said:**
> The link has been changed so here is the new link.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/367309")

What the fix is essentially the below xrandr command
```
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
```

fix worked for me

And about sound Fn Keys ? works good on your macbook 1.1 ?

---

### Post by jgould81 on 2009-05-25
Using this fixed my issue with the brightness controls... xrandr --output LVDS --set BACKLIGHT_CONTROL combination...


Sound fn keys work as well 

Model  is a Macbook 1,1.

Now to tackle the overly sensitive trackpad...

Josh

---

### Post by Richardcavell on 2009-05-25
To fix the brightness controls, add a command to System->Preferences->Startup applications that does:

xrandr --output LVDS --set BACKLIGHT_CONTROL combination

Richard

---

### Post by cyberdork33 on 2009-05-26
> **Richardcavell said:**
> To fix the brightness controls, add a command to System->Preferences->Startup applications that does:

xrandr --output LVDS --set BACKLIGHT_CONTROL combination

Richard
I'd suggest adding this to the wiki page for the Macbook1,1:
[https://help.ubuntu.com/community/MacBook1-1/Jaunty](https://help.ubuntu.com/community/MacBook1-1/Jaunty)

---

### Post by slick666 on 2009-08-05
Added a section to the wiki page. Is there anything I need to do to move it from the draft wiki page to the real thing so folks can find it?

---

