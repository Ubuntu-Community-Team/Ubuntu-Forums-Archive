---
title: "intermittent mad keyboard repeat"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-07
Feisty Fawn 7.04 x64. Seemingly randomly, keys repeat extremely rapidly. I have noticed it happen when typing forum posts in Firefox.

iiiiiiiiiiiiiiiiiiiiiiiiiitttt rrrrrrrrresssuuuuuuuulllltsss in text like this, even when typing very quickly

Wondered if this was a known problem?

---

### Post by hillbilly on 2007-06-07
stupid question probably, but are you using a wireless keyboard ? Maybe the battery is down.

---

### Post by ecs_pf5 on 2007-06-08
Sorry, should have posted the details. No, 'fraid not - it's a:

```

Microsoft Comfort Curve Keyboard 2000 v1.0 
model 1047 
Product ID 76914-545-2108476-00537
KU0459
MS Part No X802646-001

```

In dpkg-reconfigure xserver-xorg it came up as a 105 type keyboard

It is a USB type. One of [these](http://www.microsoft.com/products/info/product.aspx?view=22&pcid=529e6bca-e6cf-46de-90b0-fa958a1dace8&type=ovr#PrinterFriendly)

---

### Post by MadTxn on 2007-06-13
I had this problem in Edgy, and fixed it by going to a beta feisty kernel.  I upgraded to Feisty, and it's back.  It also misses keys.  I'm on an HP Pavilion dv8000.

---

### Post by Magneto on 2007-06-14
Same problem here. No errors in relevant logs. I can't live without repeat since it makes using a terminal within Gnome painful as hell. I've disabled repeat from the Keyboard config app but I'd like to know precisely why this is happening.

---

### Post by ecs_pf5 on 2007-06-17
Which logs would I be best looking in, maybe I can see something on my mmmmmachine. See.. it's still doing it :lol:

---

### Post by schorsch on 2007-06-17
Is this happening in a console terminal, too? You can get one by holding CTRL-ALT-F2 at the same time. If not you should take a look in the Xorg-logfiles. Otherwise the output of the "dmesg" command could be helpful.

---

### Post by MAZDA on 2007-06-17
> **ecs_pf5 said:**
> Feisty Fawn 7.04 x64. Seemingly randomly, keys repeat extremely rapidly. I have noticed it happen when typing forum posts in Firefox.

iiiiiiiiiiiiiiiiiiiiiiiiiitttt rrrrrrrrresssuuuuuuuulllltsss in text like this, even when typing very quickly

Wondered if this was a known problem?

For some reason this problem exist since 2004/2005 for nearly every type of keyboard !

Noname keyboard keys repeating randomly
[http://ubuntuforums.org/showthread.php?t=19233](http://ubuntuforums.org/showthread.php?t=19233)

---

### Post by ecs_pf5 on 2007-06-17
> 
Is this happening in a console terminal, too?
yes, pretty much anywhere you can type something, it will do it.. completely at random, when it feels like it.

[edit]

AH.. I just did the ctrl-alt-f2 

No.. no I've never seen it do it in a proper terminal window.

I thought you meant a GUI terminal, it was a bit of a shock when I ctrl-alt-f2'd and the screen went entirely black lol

Wondering.. is this tying in with my desktop lockup problems.. i.e. some kind of misconfiguration with the dodgy radeon x70000 driver maybe

Ah.. thanks MAZDA, just read the numerous bug reports.

---

### Post by schorsch on 2007-06-17
Uhm, I forgot to mention the way to come back to the GUI, sorry ;)

```
CTRL-ALT-F7
```

But if the error does not exit in a console terminal session, I guess it is the xorg-driver oder the xorg-config that is causing the trouble. You should take a look in the logs under /var/log to get a hint what is going wrong with your keyboard.

---

### Post by ecs_pf5 on 2007-06-17
Will I be okay to delete the contents of the log files and save them as 'empties' - I've been taking the 'try and break it' approach to learning Ubuntu, so it's be kinda handy to 'start afresh' with the logs if possible?

eek.. did it anyway for better or worse

here's just the errors and warnings out of xorg.0.log

```

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "UseFBDev" is not used
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : No such file or directory
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

```In the process of seeing what else I can find.

Nothing else obvious to a n00b I can see.

There's some stuff in var/log/installer/hardware-summary about the mouse and keyboard if that suggests anything, but it kinda looks sort of right to me?

(but i wouldn't really know)

```

/proc/bus/input/devices: I: Bus=0017 Vendor=0001 Product=0001 Version=0100
/proc/bus/input/devices: N: Name="Macintosh mouse button emulation"
/proc/bus/input/devices: P: Phys=
/proc/bus/input/devices: S: Sysfs=/class/input/input0
/proc/bus/input/devices: H: Handlers=mouse0 event0 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=70000 0 0 0 0
/proc/bus/input/devices: B: REL=3
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0003 Vendor=046d Product=c408 Version=0110
/proc/bus/input/devices: N: Name="Logitech USB Trackball"
/proc/bus/input/devices: P: Phys=usb-0000:00:1d.0-1/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input1
/proc/bus/input/devices: H: Handlers=mouse1 event1 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=1f0000 0 0 0 0
/proc/bus/input/devices: B: REL=3
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0003 Vendor=045e Product=00dd Version=0111
/proc/bus/input/devices: N: Name="Microsoft Comfort Curve Keyboard 2000"
/proc/bus/input/devices: P: Phys=usb-0000:00:1d.0-2/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input2
/proc/bus/input/devices: H: Handlers=kbd event2 
/proc/bus/input/devices: B: EV=120003
/proc/bus/input/devices: B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
/proc/bus/input/devices: B: LED=107
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0003 Vendor=045e Product=00dd Version=0111
/proc/bus/input/devices: N: Name="Microsoft Comfort Curve Keyboard 2000"
/proc/bus/input/devices: P: Phys=usb-0000:00:1d.0-2/input1
/proc/bus/input/devices: S: Sysfs=/class/input/input3
/proc/bus/input/devices: H: Handlers=kbd event3 
/proc/bus/input/devices: B: EV=10000f
/proc/bus/input/devices: B: KEY=7fff002c3027 bf00444000000000 1 10f808807c407 ffe77bfad9715fff febeffdfffefffff fffffffffffffffe
/proc/bus/input/devices: B: REL=40
/proc/bus/input/devices: B: ABS=100000000

```

---

### Post by jrlii on 2007-06-17
I had this problem with a cheap wally world keyboard, not as bad with Ubuntu as with MEPIS, but still there. No problems since upgrading(?) to an IBM 1391401 "Model M" keyboard from 1988.

Microsoft's keyboards are not that much different from the no-names.

If you want to get a new bullet proof keyboard, check out the Unicomp clicky keyboards. It might be the last keyboard you ever need to buy.

---

### Post by ecs_pf5 on 2007-06-17
I'll try another keyboard.. haven't another usb one but I'm sure I have a ps2 one somewhere

[edit]

okay, now I have a

Packard Bell
model no 5131c
fcc id E5XKBM10510
P/N 1200610001

ps2 keyboard.

[edit]

no joy, still doing it, at random.

Flightgear seems to kick it off, make it worse.. I'll try rebooting fully and doing a session without starting it

Right, I've done a complete power-down plug-out-of-the-wall reboot and have booted baccck iiiinnnnto firefox without runnimng

- nope, there it is, doesn't look like it's caused by remnants of flightgear :(

Not the keyboard itself, not flightttgear / other apps.. I'm stumped. Guess I have to look closer at the video driver setup.

---

### Post by foresto on 2008-05-16
Is this the same problem as reported in [this thread?](http://ubuntuforums.org/showthread.php?t=772773)

---

