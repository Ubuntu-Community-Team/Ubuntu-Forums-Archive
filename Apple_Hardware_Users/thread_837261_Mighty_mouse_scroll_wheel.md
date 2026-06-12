---
title: "Mighty mouse scroll wheel"
date: 2008-06-22
forum: Apple Hardware Users
---

### Post by erdah on 2008-06-22
Hi!

I have installed Ubuntu hardy on my new 24" aluminum imac. I'm using the wireless aluminum keyboard and wireless mighty mouse. The mouse and keyboard worked from scratch but not the scroll wheel. (Scroll wheel click is working.) I have read and followed A LOT of threads and how-tos about this but with no success.

In my xorg.conf I've tried all kinds of wheel options, ZAxisMapping, evdev/mouse drivers, protocols etc.

Here are a few system outputs:

```

This is my xorg.conf for the moment ->
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "RelHWHEELOptions" "invert"
        Option          "Buttons" "8"
        Option          "CorePointer"
        Option          "ZAxisMapping" "5 6 7 8"
EndSection

```

```

$ dmesg | grep mouse
[   27.061532] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.072756] mice: PS/2 mouse device common for all mice

```

Any ideas?

---

### Post by Brightbelt on 2008-06-22
Just thought I'd lend some sympathy. I've encountered the exact same thing. I can even right-click with my mighty mouse, but the scroll does not function.

Btw, in case you think this is solely an apple-related problem, I tried using a Microsoft bluetooth mouse and the same thing happened. Everything worked but the scroll.  

So this must be about scrolling with bluetooth. I do use a usb signal Kensington mouse and the scroll works fine with that mouse in Ubuntu. I just wish I could use bluetooth to keep that Usb port free. 

Good Luck. I'll keep an eye on this thread. Thanks for starting this thread.
Frank B.

---

### Post by erdah on 2008-06-25
Thanks for your reply. Seems like the problem is in blueZ. The extra bytes containing the scroll information is never sent. Is there an easy way to install the latest blueZ package? Maybe from intrepid ibex?

---

### Post by RRR-007 on 2008-07-03
Any updates on this? Got your wheels scrolling? if so throw out the soln plz......

---

### Post by erdah on 2008-07-03
I'm afraid not. I'll post here as soon as I find a solution.

---

### Post by fahrstuhl on 2008-07-07
I had a similar bug with my Microsoft IntelliMouse. I solved it by using the evdev driver, uninstalling imwheel and deleting the imwheel file in /etc/X11/xinit/xinitrc.d

This file executed Xmodmap on X startup and remapped my mouse buttons in a wrong way. (Remapping seems to be unnecessary with the evdev driver.)

my X.org conf for the sake of completeness:

```

Section "ServerLayout"

    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "SendCoreEvents"
    InputDevice    "Keyboard0" "SendCoreEvents"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"

EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Device" "/dev/input/event4"
EndSection

```

---

### Post by enigma_0Z on 2008-10-03
> **fahrstuhl said:**
> I had a similar bug with my Microsoft IntelliMouse. I solved it by using the evdev driver, uninstalling imwheel and deleting the imwheel file in /etc/X11/xinit/xinitrc.d

This file executed Xmodmap on X startup and remapped my mouse buttons in a wrong way. (Remapping seems to be unnecessary with the evdev driver.)

my X.org conf for the sake of completeness:

```

Section "ServerLayout"

    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "SendCoreEvents"
    InputDevice    "Keyboard0" "SendCoreEvents"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"

EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Device" "/dev/input/event4"
EndSection

```

Hmm, unfortunately the evdev driver works a bit differently, and the device node will change for mighty-mice, because they're wireless and hotplugged...

And it doesn't (to my knowledge) get a link in /dev/input/by-name, so that doesn't work with evdev either. Anyone know of an updated method for hardy?

---

### Post by tubasoldier on 2008-10-06
The only way to get the scrollwheel working is to use bluetooth directly. By doing so, it will disable your wireless keyboard, a non-issue if you have the usb keyboard. There is a great thread on here as how to set up a wireless bluetooth keyboard.
[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

I'm using KDE so i'm not certain as to how to accomplish it in Gnome, but I've just got mine all working properly this evening.

---

### Post by hajk on 2008-10-06
Yes, activate the scrollball through Bluetooth. I found it easiest to first pair the mouse in Mac OS X, then reboot GNU/Linux and follow the recipe:

1. Make sure the packages "bluetooth", "bluez-utils" and (in Gnome) "bluez-gnome" are installed.

2. Reset the mouse and get its MAC address```

$ sudo hciconfig hci0 reset
$ sudo hcitool scan
```and write it down (six hex digits like 00:1F:F3:....).

3. Add the line```

options hci_usb reset=1
```to the file /etc/modprobe.d/options. This will reset the mouse on boot if it's not done by the kernel.

4. Edit /etc/default/bluetooth to read```

BLUETOOTH_ENABLED=1
HID2HCI_ENABLED=0
HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:1F:F3... --master --server"
```where you should of course substitute the 6-digit hex address of your own mouse. After a reboot, the Gnome Bluetooth applet will ask for the pairing key, 0000 if you didn't change it in Mac OS X.

That should be it, enjoy!

---

### Post by cyberdork33 on 2008-10-06
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

---

### Post by hajk on 2008-10-06
> **cyberdork33 said:**
> [http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)
Right, I forgot about that -- now fixed.

---

### Post by cyberdork33 on 2008-10-06
> **hajk said:**
> Right, I forgot about that -- now fixed.
Oh, I actually corrected something else, but then determined I was wrong, then posted that link instead for reference since I knew that it worked. I didn't even notice you skipped the reset command. :)

---

