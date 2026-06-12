---
title: "Easily save a few extra watts when idle and increase your battery life!"
date: 2009-05-26
forum: Apple Hardware Users
---

### Post by volanin on 2009-05-26
Ubuntu is already very good at energy-saving while your macbook is idle. But there are some extra watts you can easily save to increase battery time even more! Two of the most common are:


**1. Disable wireless if you don't need it!**

Even if you aren't connected to a wireless network, your adapter is still sitting there using about 2 watts of power for nothing. To prevent it from wasting this energy, you can unload the driver/module from the system, effectively turning off the device.

To make this process very easy, copy the following lines into a script and create an icon for it in the desktop or the panel. Everytime you run it, it will load or unload the driver/module, turning the wireless adapter on/off!

```
lsmod | grep -q ath9k
if [ $? == 0 ]; then
  zenity --question --text "Do you want to turn wireless OFF?"
  if [ $? == 0 ]; then gksudo rmmod ath9k; fi
else
  zenity --question --text "Do you want to turn wireless ON?"
  if [ $? == 0 ]; then gksudo modprobe ath9k; fi
fi
```


**2. Properly enable USB autosuspend!**

The macbook is mostly USB based. The keyboard, the trackpad and almost every other device in the machine uses the USB bus to operate. You can easily save another 1-2 watts of power by allowing linux to suspend the USB devices when they are idle. This is exacly what powertop does when you press the 'U' key, but it is not enabled by default every boot.

Copy the lines below to the beginning of your */etc/rc.local* file:

```
for DEVICE in /sys/bus/usb/devices/*; do
  if [ -w $DEVICE/power/autosuspend ]; then
    echo 0 > $DEVICE/power/autosuspend
  fi

  if [ -w $DEVICE/power/level ]; then
    echo auto > $DEVICE/power/level
  fi
done
```


This should do it!
I hope you can enjoy the extra battery time you'll get!

---

### Post by cyberdork33 on 2009-05-26
Thanks.

Just a note, this should work for other systems too (may need to change the wireless driver your your specific driver though)

also, bluetooth is another power waster if you are not using it.

---

### Post by stream303 on 2009-05-26
You can save 2 more watts by not having a blinking cursor - even if you don't use a terminal.

Go into your keyboard prefs, and make sure that "Cursor Blinks in Text Fields" is unchecked.

I didn't believe it myself until I measured it with an AC wattmeter at the outlet.

---

### Post by tiagobt on 2009-06-23
The script to disable wireless doesn't seem to work in KDE. Regardless of the state of the driver, the script always asks "Do you want to turn wireless ON?". Clicking on "OK" doesn't change the state of the driver. I've tried to replace **gksudo** by **kdesudo**, but the result was the same. For some reason, running the script from a terminal window (**./wireless.sh**) works fine, but clicking on a desktop icon produces the behavior I described.

Is this issue specific to KDE? Anyway to fix it?

Thanks!

---

### Post by Richardcavell on 2009-06-24
Another tip on batteries:

In March 2009, Apple released an update that increases the time that a battery will hold its charge when the system is turned off.  It must be run under OS X, but an Ubuntu user will reap the benefits once it's installed, of course:

[http://www.apple.com/downloads/macosx/apple/firmware_hardware/batteryupdate14.html](http://www.apple.com/downloads/macosx/apple/firmware_hardware/batteryupdate14.html)

Richard

---

### Post by pedrogfrancisco on 2009-08-15
USB autosuspend will sometimes trigger issues on the 2.6.30 kernels, see ["mouse and kernel 2.6.30" on "Karmic Koala Testing and Discussion"]("http://ubuntuforums.org/showthread.php?p=7791882#post7791882").

---

