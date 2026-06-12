---
title: "Best graphics tablet?"
date: 2005-06-23
forum: Art &amp; Design
---

### Post by drummer on 2005-06-23
Hi all, 
I'm looking for a graphics tablet to have a play with and do some casual gimp work  and need to know what brands / models will work the best with Ubuntu. I won't get anything too fancy at this point and I'd like to pay only $30 or so for a small one (A5) but any info / suggestions / experience you have would be appreciated.
Thanks, drummer.

---

### Post by archibald on 2005-06-23
hey!
I've got a graphire3 A5, and it "works".

- I hear that it is possible to hack the pressure sensitivity into working, but its quite complicated and the methods change with every upgrade/date. 

- The second and main problem is that sometimes you are at the top left hand of the screen with your arrow, but just somewhere inbetween the middle and the corner on your tablet...
let me try again :D...you hit the edge of the screen with the mouse-arrow before you hit the edge of the tablet with your pen, and vise versa. This can get VERY frustrating...

These may just be  setting/configuration things, but I think basicly the problem is that the tablet is being run as a "mouse" with local and not global transformation of the arrow according to the pen... (it has been detected correctly mind you! I'm using the right drivers, etc!)

-the included "mouse for the tablet" works fine, but the scrollwheel-directions are the wrong way around...up is down, down is up


anyhow, what I'm trying to say is, it works, but it doesnt work well, at least not without a lot of tweaking, and this is the most common brand (wacom), so any other brand will be much worse!

my two cents: the wacom graphire series are the best tablets there are for linux, but the general experience would be much better on windows/OSX, as the proprietary drivers far surpass what the OS people have come up with to date!


cheers, hope that helped!

n.

---

### Post by tube on 2005-06-25
No major problems with my Wacom Intuos 2 A4-tablet here. Pressure sensitivity works just fine. The only thing I had to do to make it behave was to add the InputDevice sections into xorg.conf, like this:

```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
        Option          "USB"           "on"
        Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "20"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
        Option          "USB"           "on"
        Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "20"
EndSection
```

You'll also need to add the devices into the ServerLayout, like this:

```
Section "ServerLayout"
        ...
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection
```

You might need to enable TiltInvert or twiddle with the Threshold value.

I have no idea if this works for Graphire too, but it's worth a shot, right? :wink:

---

### Post by Waqas on 2005-09-11
Theres tones of reviews in cgtalk.com, and all says nothing better than a Wacom tablet. I guess they are all right.. Me also using an A5 Graphire 3 Wacom tablet. There is also a review comparison between Wacom, Trust and one more brand that I cant recall on Anandtech forum.. Also the same result, Wacom always lead.

---

### Post by benplaut on 2005-09-11
the cheapest you'll find is an Intuos3, for about $100 USD...

i have an Intuos2 that works just fine  :)

---

### Post by drummer on 2005-09-11
[QUOTE=benplaut]the cheapest you'll find is an Intuos3, for about $100 USD...

i have an Intuos2 that works just fine  :)[/QUOTE]
 I got a Wacom PenPartner 2 weeks ago for $15 to play with and it's working pretty well, pressure sensitivity isn't working though, when the pressure sensitivity option is checked in Gimp it doesn't draw anything.. just random infrequent dots. I haven't tried the threshold settings in the above post but will do at some point. The intuos looks like a good option in the future when I have money to spare.

---

### Post by Deeze on 2005-09-12
I have an Intuos and Graphire (both original versions) that work perfectly.

---

