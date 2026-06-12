---
title: "Macbook keyboard not working"
date: 2011-12-09
forum: Apple Hardware Users
---

### Post by DARKAD on 2011-12-09
At the graphic login time the macbook keyboard works.
After it doesn't work.

Ubuntustudio 11.10 64bit - xfce - macbook 4.1

```
tail /var/log/Xorg.0.log
```

[   388.067] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[   388.067] (**) Option "xkb_rules" "evdev"
[   388.067] (**) Option "xkb_model" "pc105"
[   388.067] (**) Option "xkb_layout" "it"
[   388.067] (EE) HID 04f3:0103: failed to initialize for relative axes.
[   388.067] (II) HID 04f3:0103: initialized for absolute axes.
[   388.067] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[   388.067] (**) HID 04f3:0103: (accel) acceleration profile 0
[   388.067] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[   388.067] (**) HID 04f3:0103: (accel) acceleration threshold: 4

```
dpkg-reconfigure console-setup
``` it didn't ask me anything about keyboard.

```
sudo dmesg | grep Keyboard
```

[    1.776755] generic-usb 0003:05AC:1000.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0000:00:1a.0-1/input0
[    2.623739] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input6
[    2.623822] apple 0003:05AC:022A.0004: input,hidraw3: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
[    2.630489] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input7
[    2.630592] apple 0003:05AC:022A.0005: input,hidraw4: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input2
[  344.643401] generic-usb 0003:04F3:0103.0006: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:1d.0-1/input0
[  387.710679] generic-usb 0003:04F3:0103.0008: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:1a.0-2/input0
[ 1705.573924] generic-usb 0003:05AC:1000.000A: input,hidraw5: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0000:00:1a.0-1/input0

From the root /
```
find -type f -name 'xorg.conf'
```
it didn't find anything.

in the attachment there are /etc/default/console-setup and /etc/default/keyboard.

May someone help me?

---

### Post by -nat- on 2011-12-09
I have the same issue. It only began a couple of days ago, yet I don't remember updating any software or changing any preferences that would cause this problem. In past versions of Ubuntu turning numlock on/off (as suggested [here]("http://ubuntuforums.org/showthread.php?t=1360308&page=2")) always worked, but no longer seems to.

Macbook 3,1 Ubuntu 11.10, 32bit, XFCE

---

### Post by DARKAD on 2011-12-10
I'm looking at this: [https://help.ubuntu.com/community/AppleKeyboard]("https://help.ubuntu.com/community/AppleKeyboard")

Hope it helps!

---

### Post by -nat- on 2011-12-10
> **DARKAD said:**
> I'm looking at this: [https://help.ubuntu.com/community/AppleKeyboard]("https://help.ubuntu.com/community/AppleKeyboard")

Hope it helps!

Thanks - the suggestion at the bottom of that page to double tap fn-f6 fixed the issue for me!

---

### Post by DARKAD on 2011-12-10
Thank you -nat- !
It works for me too!

---

### Post by camratcliffe on 2013-03-04
fn F6 - this finally has me typing on my macbook keyboard again. Whoda thunk!

---

