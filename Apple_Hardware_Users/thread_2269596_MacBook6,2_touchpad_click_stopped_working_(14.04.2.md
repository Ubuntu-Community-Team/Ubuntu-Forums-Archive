---
title: "MacBook6,2 touchpad click stopped working (14.04.2 LTS)"
date: 2015-03-16
forum: Apple Hardware Users
---

### Post by derek.x.kwan on 2015-03-16
(MacBookPro6,2, not MacBook6,2 sorry)


Hello,

I've been running Ubuntu Studio on my MBP for about a month or so relatively smoothly and just today I've lost the clicking ability on my touchpad. For a little bit, even the touchpad didn't move the cursor, but after a few restarts I've managed to get that back. Even in the login screen the clicking doesn't work. I've recently installed the latest updates and I'm currently running 14.04.2 LTS on the 3.13.0-46-lowlatency kernel. I've plugged in an external mouse and it works great but I'd like to get my touchpad clicking back.

Here are the relevant logs from my Xorg.0.log

```

[    20.680] (II) config/udev: Adding input device bcm5974 (/dev/input/event12)
[    20.680] (**) bcm5974: Applying InputClass "evdev touchpad catchall"
[    20.680] (**) bcm5974: Applying InputClass "touchpad catchall"
[    20.680] (**) bcm5974: Applying InputClass "Default clickpad buttons"
[    20.680] (**) bcm5974: Applying InputClass "Disable clickpad buttons on Apple touchpads"
[    20.680] (II) LoadModule: "synaptics"
[    20.681] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.681] (II) Module synaptics: vendor="X.Org Foundation"
[    20.681]    compiled for 1.15.0, module version = 1.7.4
[    20.681]    Module class: X.Org XInput Driver
[    20.681]    ABI class: X.Org XInput driver, version 20.0
[    20.681] (II) Using input driver 'synaptics' for 'bcm5974'
[    20.681] (**) bcm5974: always reports core events
[    20.681] (**) Option "Device" "/dev/input/event12"
[    20.714] (II) synaptics: bcm5974: found clickpad property
[    20.714] (--) synaptics: bcm5974: x-axis range -4460 - 5166 (res 0)
[    20.714] (--) synaptics: bcm5974: y-axis range -75 - 6700 (res 0)
[    20.714] (--) synaptics: bcm5974: pressure range 0 - 256
[    20.714] (--) synaptics: bcm5974: finger width range 0 - 16
[    20.714] (--) synaptics: bcm5974: buttons: left double triple
[    20.714] (--) synaptics: bcm5974: Vendor 0x5ac Product 0x236
[    20.714] (**) Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
[    20.714] (--) synaptics: bcm5974: touchpad found
[    20.714] (**) bcm5974: always reports core events
[    20.725] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.2/input/input12/event12"
[    20.725] (II) XINPUT: Adding extended input device "bcm5974" (type: TOUCHPAD, id 11)
[    20.725] (**) synaptics: bcm5974: (accel) MinSpeed is now constant deceleration 2.5
[    20.725] (**) synaptics: bcm5974: (accel) MaxSpeed is now 1.75
[    20.725] (**) synaptics: bcm5974: (accel) AccelFactor is now 0.017
[    20.725] (**) bcm5974: (accel) keeping acceleration scheme 1
[    20.725] (**) bcm5974: (accel) acceleration profile 1
[    20.725] (**) bcm5974: (accel) acceleration factor: 2.000
[    20.725] (**) bcm5974: (accel) acceleration threshold: 4
[    20.726] (--) synaptics: bcm5974: touchpad found
[    20.726] (II) config/udev: Adding input device bcm5974 (/dev/input/mouse2)
[    20.726] (**) bcm5974: Ignoring device from InputClass "touchpad ignore duplicates"



```


Thanks in advance for the help!

---

