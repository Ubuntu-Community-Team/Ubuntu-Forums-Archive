---
title: "Apple Cinema Display Brightness on Ubuntu Desktop"
date: 2016-03-14
forum: Apple Hardware Users
---

### Post by tim8 on 2016-03-14
I was gifted a 27" Apple Cinema Display, which I have connected to my Ubuntu desktop via displayport on a NVIDIA 760 Graphics Card (displayport -> minidisplayport adapter which the display plugs into).

Everything seems to be working fine, except that I cannot control the backlight brightness of the Apple monitor, and it is currently quite dim. I can control the brightness of the image being sent from the graphics card (and the contrast etc) - but that doesn't make up for having a backlight that is currently set to low.

I tried downloading acdcontrol, which is recommended to solve this. However, I can't find this monitor anywhere in /dev/ - so I don't know which driver to point at as the target of the acdcontrol setting. The two recommended options /dev/usb/hiddev0 and /dev/usb/hiddev1 are my keyboard and mouse. I assume this has something to do with me plugging the monitor in via displayport? Would there be an entry in /dev for displayport connections?

Alternatively, is there any other way to increase the brightness of the Apple Monitor? If I borrow a mac and increase the brightness, will it save that setting when I plug the linux machine back in? What else should I try?

Thanks!

---

### Post by slickymaster on 2016-03-14
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by tim8 on 2016-03-15
I've found the solution - posting it here for others:

The USB from the monitor needs to also be plugged into the computer (why I hadn't thought of this I don't know) -- then acdcontrol should be able to find the monitor. I haven't been able to get the monitor to maximum brightness yet (though I think another workaround for this exists online).

The other solution also works --- plug the monitor into a mac computer temporarily and change the background brightness. The monitor should preserve the status when it is plugged back into the linux box.

---

