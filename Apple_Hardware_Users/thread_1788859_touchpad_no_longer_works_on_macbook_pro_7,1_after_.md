---
title: "touchpad no longer works on macbook pro 7,1 after upgrade to 11.04"
date: 2011-06-23
forum: Apple Hardware Users
---

### Post by phrawzty on 2011-06-23
Hello,

After having successfully run Ubuntu 10.x on my Macbook Pro 7,1 for quite some time, I decided to upgrade to 11.04 today.  Everything appears to work except for one thing : the trackpad.

Unlike some of the other threads which report unstable or inconsistent behaviour, my condition is entirely consistent : it simply doesn't work.  No clicking, no scrolling, no moving of the pointer - it is as if the trackpad doesn't exist.

```
$ sudo dmidecode -s system-product-name
MacBookPro7,1
```

```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 05ac:820b                           	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Built-in iSight                         	id=10	[slave  keyboard (3)]
    &#8627; HID 05ac:820a                           	id=12	[slave  keyboard (3)]
    &#8627; Apple Inc. Apple Internal Keyboard / Trackpad	id=11	[slave  keyboard (3)]
```

```
$ dmesg | grep -i trackpad
[   13.279440] input: Apple Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:06.0/usb4/4-3/4-3:1.0/input/input10
[   13.279664] apple 0003:05AC:0237.0001: input,hidraw2: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:06.0-3/input0
[   13.293120] apple 0003:05AC:0237.0002: hidraw3: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:06.0-3/input1
```

```
$ sudo tpconfig 
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
```

```
$ lsusb | grep -i trackpad
Bus 004 Device 002: ID 05ac:0237 Apple, Inc. Internal Keyboard/Trackpad (ISO)
```

```
$ lsmod | grep -i apple
hid_apple              13324  0 
hid                    91020  2 hid_apple,usbhid
applesmc               19604  0 
input_polldev          14007  1 applesmc
```

I am open to any ideas. :)

Thank you !

---

### Post by johnmurrayvi on 2011-06-23
What does your xorg.conf look like?
Also, what does this give you:
```
cat /var/log/Xorg.0.log | grep -i trackpad
```

---

### Post by LtPitt on 2011-06-24
I am not seriously skilled to help but I'd try a live 11.04 cd and check if the trackpad works from there.
If so I'd just reinstall it from scratch: not always an upgrade works flawlessly (in my experience).

Good luck with your hunt anyway :)

---

### Post by phrawzty on 2011-07-26
> **johnmurrayvi said:**
> What does your xorg.conf look like?
Also, what does this give you:
```
cat /var/log/Xorg.0.log | grep -i trackpad
```

I've attached my xorg.conf(.txt) - nothing special as far as i can see.

As for the Xorg.log, the trackpad is clearly identified (which is a good thing) :
```

$ cat /var/log/Xorg.0.log | grep -i trackpad
[    43.170] (II) config/udev: Adding input device Apple Inc. Apple Internal Keyboard / Trackpad (/dev/input/event10)
[    43.170] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Applying InputClass "evdev keyboard catchall"
[    43.170] (II) Using input driver 'evdev' for 'Apple Inc. Apple Internal Keyboard / Trackpad'
[    43.170] (**) Apple Inc. Apple Internal Keyboard / Trackpad: always reports core events
[    43.170] (**) Apple Inc. Apple Internal Keyboard / Trackpad: Device: "/dev/input/event10"
[    43.210] (--) Apple Inc. Apple Internal Keyboard / Trackpad: Found keys
[    43.210] (II) Apple Inc. Apple Internal Keyboard / Trackpad: Configuring as keyboard
[    43.210] (II) XINPUT: Adding extended input device "Apple Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD)

```

Still no activity from once i'm in X, though. :(

---

### Post by phrawzty on 2011-07-26
> **phrawzty said:**
> I've attached my xorg.conf(.txt) - nothing special as far as i can see.
In fact, on second look, that's not true - the trackpad section at the end is, in fact, superfluous.  After commenting it and rebooting my trackpad became operational (yay).

---

### Post by martin7890 on 2012-08-10
[Thanks phrawzty!]("http://ubuntuforums.org/member.php?u=83427")
I had the same issue (after an update from 11.10 to 12.04) and commenting it out the trackpad section in the xorg.conf solved the problem!

Thanks so much!

---

