---
title: "how to disable tapping"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by kristiansuhl on 2007-02-26
I have installed Ubuntu a while ago and it is my first GNU+Linux distribution ever. There is a big problem for me that keeps me from learning more by navigating around: When I try to navigate in the system I get problem with the tapping-function and it is driving me crazy! It's constantly closing or minimizing programs. 

I have a HP computer with a synaptics touchpad and UBUNTU with GNOME. 

Does anybody know how to disable this horrific function of tapping?

---

### Post by NewOldTimer on 2007-02-26
see here...[http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/)

Edit- sorry thats for disabling the touch pad

try here...[http://www.newlinuxuser.com/howto-disable-the-tap-function-on-my-touchpad/](http://www.newlinuxuser.com/howto-disable-the-tap-function-on-my-touchpad/)

---

### Post by kristiansuhl on 2007-02-27
I hope I will fix it now, thank you very much!

---

### Post by Bachstelze on 2007-02-27
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Modify your xorg.conf as explained and install gsynaptics, it will let you configure your touchpad more precisely, including disabling tapping.

---

### Post by jay019 on 2007-03-05
Sweet. I was hoping this would be possible.

Is there any way to automate this when a USB mouse is plugged in?

---

### Post by twisted_steel on 2007-03-05
> **jay019 said:**
> Sweet. I was hoping this would be possible.

Is there any way to automate this when a USB mouse is plugged in?


Maybe you could use hotplug to detect the mouse and execute the *synclient* command?  This page has an example of removing the kernel module, which is probably too much: [http://www.wlug.org.nz/HotPlugNotes](http://www.wlug.org.nz/HotPlugNotes).

This is a complete guess right now, as I'm headed off to bed, but maybe something along these lines:

```

/etc/hotplug/usb/usbmouse:
 #!/bin/sh

# use synclient to toggle the touchpad status
# when the mouse is plugged in and removed

if test "$ACTION" = "add"  ; then
    synclient TouchpadOff=1
elif test "$ACTION" = "remove" ; then
    synclient TouchpadOff=0
# else unknown action?
fi
```Maybe someone else has an idea; I'll check back tomorrow :)

---

### Post by twisted_steel on 2007-03-06
Hmm, it seems hotplug is no longer in Edgy - it was replaced with udev.

---

### Post by jay019 on 2007-03-06
Yeah, I tried looking at udev rules, but cant quite work it out.

All I know about my mouse is this...

> 
ID 04d9:0499 Holtek Semiconductor, Inc


And lsusb tells me it usually resides here...

> 
Bus 003 Device 004:



[COLOR="Red"]EDIT: Unplugging then replugging the device changed the above line to...
Bus 003 Device 5:

Not sure where to go with this, I am very new to udev.[/COLOR]


How do I get the path or node for udevinfo?

Thanks

---

### Post by jay019 on 2007-03-06
Just ignore me. It seems that what i needed for my rules is...

SYSFS{idVendor}=="04d9", SYSFS{idProduct}=="0499"

Nevermind, should be able to get something going now.

---

