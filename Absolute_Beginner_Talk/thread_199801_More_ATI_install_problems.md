---
title: "More ATI install problems"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by andyb.uk on 2006-06-19
I installed Ubuntu a couple of weeks ago, and am only having one problem with this great OS- installing the ATI drivers and open GL.

I've read several other threads, and tried them all, leading to 2 reinstalls(!), but am getting nowhere.

In my xorg.conf file entry for Section "device" there seems to be two mentions of devices (sorry- I'm not sure if my attachment worked?)

The first one says the identifier is the Radeon 9200 SE, Driver ATI and the Bus ID PCI:2:0:0

The second entry:

Identifier ATIconfig-device [0]
Driver fglrx
Option videoOverlay ON
Option GLOverlay OFF


I tend to think that there should only be one entry here?

Should I change the GLOverlay to ON?

Or do I need to go right back to the beginning and start again?

Any ideas would be much appreciated!

Thanks,

---

### Post by xXx 0wn3d xXx on 2006-06-19
Install xorg-driver-fglrx (I think that is the name I am not on Ubuntu at the moment) and linux-restricted-modules for your kernel in synaptic  and then it should work.

Edit: Read [ this tutorial. ](http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue)

---

### Post by andyb.uk on 2006-06-19
Thanks for the quick response!

Here's what fglrxinfo has to say, having done what's suggested:

---

