---
title: "Keyboard not working 2.6.27-11 (20&quot; Alu iMac)"
date: 2009-01-30
forum: Apple Hardware Users
---

### Post by snek on 2009-01-30
With the new kernel my keyboard & mouse stopped working.
I am currently still bootting 2.6.27-9 and everything works fine, but when I choose -11 it doesn't work at all.
Anyone know any fixes for this?

There's no input section in my xorg.conf either, isn't that a bit strange?
I'm mostly used to working with normal PC's but got an iMac at work and have been running Ubuntu on it for about 2 months now. So far so good, until this kernel update.

---

### Post by snek on 2009-01-30
Well I just updated to the newest version of 2.6.27-11 and still no keyboard or mouse.
I have the PPA repos in my sources.list as well by the way.

For the rest my system is completely up to date.

Can anyone tell me where the keyboard settings are stored? 
I'm used to doing everything by hand and Ubuntu Intrepid seems to store a few settings in places.

---

### Post by cyberdork33 on 2009-01-30
well, technically, you shouldn't have an input section in your xorg.conf anymore, it is supposed to detect it for you.

I am going to assume this is not a wireless keyboard...

try booting with any unneeded USB devices attached and see if the problem still occurs.
Make sure that your firmware updates are up to date.

Can someone else with similar hardware confirm this issue? We need to verify that it is a bug and open a bug report if so.

---

### Post by johnlocke2342 on 2009-01-30
Just bought one yesterday for my PC desktop, in replacement of my old PS/2 keyboard. I'm french, so it's an AZERTY version.
It works fine on Windows (sic!), but Ubuntu recognizes it as an QWERTY Keyboard. Don't know how to fix this in another way than going in System>Preferences>Keyboard, and it's the same thing if I boot the 2.6.27-9 kernel.

---

### Post by snek on 2009-01-31
> **cyberdork33 said:**
> well, technically, you shouldn't have an input section in your xorg.conf anymore, it is supposed to detect it for you.

I am going to assume this is not a wireless keyboard...

try booting with any unneeded USB devices attached and see if the problem still occurs.
Make sure that your firmware updates are up to date.

Can someone else with similar hardware confirm this issue? We need to verify that it is a bug and open a bug report if so.

You are correct, it's a wired keyboard. The thin aluminum one to be exact.
I don't have any other usb devices attached to the imac (7,1 to be exact).
I haven't booted OSX in quite a while now, when I get back to work on monday I'll check for firmware updates.

---

### Post by snek on 2009-01-31
> **johnlocke2342 said:**
> Just bought one yesterday for my PC desktop, in replacement of my old PS/2 keyboard. I'm french, so it's an AZERTY version.
It works fine on Windows (sic!), but Ubuntu recognizes it as an QWERTY Keyboard. Don't know how to fix this in another way than going in System>Preferences>Keyboard, and it's the same thing if I boot the 2.6.27-9 kernel.

Ok so you are runnig a normal PC and have an AZERTY keyboard, what does that have to do with Ubuntu not detecting APPLE hardware? Please start your own topic..

---

### Post by cyberdork33 on 2009-01-31
> **snek said:**
> Ok so you are runnig a normal PC and have an AZERTY keyboard, what does that have to do with Ubuntu not detecting APPLE hardware? Please start your own topic..
I think he has an *Apple* Keyboard....

---

### Post by snek on 2009-02-02
Well I logged into OSX and checked for updates, no firmware updates available.

---

### Post by snek on 2009-02-17
I have tried the 2.6.27-3-rt kernel now, and once again no keyboard or mouse. Still stuck using 2.6.27-9 generic. Maybe I'll give the server kernel a try which I use at home on my sempron 3400+ system.  Has no one experienced this problem?  I'm running a pretty standard intrepid installation and use reFit to boot.  Linux 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux


Output from Xorg.0.log while disconnecting/reconnecting keyboard (mouse is plugged into keyboard, running 2.6.27-9-generic):
> 
(EE) Apple, Inc Apple Keyboard: Read error: No such device
(II) config/hal: removing device Apple, Inc Apple Keyboard
(II) Apple, Inc Apple Keyboard: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Apple, Inc Apple Keyboard
(**) Apple, Inc Apple Keyboard: always reports core events
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event2"
(II) Apple, Inc Apple Keyboard: Found keys
(II) Apple, Inc Apple Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Apple, Inc Apple Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Apple, Inc Apple Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Apple, Inc Apple Keyboard: xkb_layout: "us"
(**) Option "xkb_variant" "mac"
(**) Apple, Inc Apple Keyboard: xkb_variant: "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Apple, Inc Apple Keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Apple, Inc Apple Keyboard
(**) Apple, Inc Apple Keyboard: always reports core events
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event1"
(II) Apple, Inc Apple Keyboard: Found keys
(II) Apple, Inc Apple Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Apple, Inc Apple Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Apple, Inc Apple Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Apple, Inc Apple Keyboard: xkb_layout: "us"
(**) Option "xkb_variant" "mac"
(**) Apple, Inc Apple Keyboard: xkb_variant: "mac"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Apple, Inc Apple Keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Primax Electronics Apple Optical USB Mouse
(**) Primax Electronics Apple Optical USB Mouse: always reports core events
(**) Primax Electronics Apple Optical USB Mouse: Device: "/dev/input/event3"
(II) Primax Electronics Apple Optical USB Mouse: Found x and y relative axes
(II) Primax Electronics Apple Optical USB Mouse: Found 4 mouse buttons
(II) Primax Electronics Apple Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Primax Electronics Apple Optical USB Mouse" (type: MOUSE)
(**) Primax Electronics Apple Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Primax Electronics Apple Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
I will try to translate this to my own Xorg.conf setup, tired of having to rely on ubuntu's own buggy detection methods.

EDIT: Nope changing Xorg.conf has no effect, server kernel didn't help either.. This really, really confuses me.. To make things even worse, I tried to hook up a normal USB keyboard & mouse and those didn't work either. Could it be that the USB hub in the iMac is not recognised???

---

### Post by cyberdork33 on 2009-02-17
> **snek said:**
> Nope changing Xorg.conf has no effect, server kernel didn't help either.. This really, really confuses me.. To make things even worse, I tried to hook up a normal USB keyboard & mouse and those didn't work either. Could it be that the USB hub in the iMac is not recognised???
It sounds like something is not working properly in the kernel you are attempting to use. There likely needs to be a bug filed if you have tried several keyboards (non-Apple as well?) and you still have this problem. You could also try to use the kernel from Jaunty to see if you have the same problem there.

---

### Post by snek on 2009-02-26
I found 2 config files in /boot for the 2 kernels.. Output:

```

 diff config-2.6.27-9-generic config-2.6.27-11-generic 
56c56
< # CONFIG_ACPI_TOSHIBA is not set
---
> CONFIG_ACPI_TOSHIBA=m
2930c2930
< CONFIG_TLSUP=m
---
> # CONFIG_TLSUP is not set
3078d3077
< # CONFIG_USB_ISP1760_PCI is not set
3217c3216
< CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.27-9.19-generic"
---
> CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.27-11.27-generic"
3423a3423
> CONFIG_X86_RESERVE_LOW_64K=y

```

I will try making some changes to the -11 config to match the -9 config and see if that maybe helps..
Also have jaunty repo's in my sources.list now, with priority pinning in place, so I'll see what kernel I can install from there.

---

### Post by cyberdork33 on 2009-02-26
> **snek said:**
> I will try making some changes to the -11 config to match the -9 config and see if that maybe helps..
Also have jaunty repo's in my sources.list now, with priority pinning in place, so I'll see what kernel I can install from there.
be careful when doing that, you could end up having serious problems if other stuff tries to get updated.

I added some stuff to the bug report you filed since you only filed it against mactel-support (not really helpful by itself).

---

