---
title: "Macbook Pro- Santa Rosa - 7.10 Gold"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by DrCR on 2007-10-19
Let's keep the 7.10 Santa Rosa MacBook Pro general discusstion in this thread (my proposal anyway. Mods, do as you will :) ).
Original Thread: [Macbook Pro- Santa Rosa](http://ubuntuforums.org/showthread.php?t=474144)


Just installed the x86 version from the Desktop LiveCD to [my MBRed setup](http://www.linuxforums.org/forum/installation/105234-howto-osx-winxp-vista-grub-hiding-linux-one-hard-drive.html).

Right-Click -- I've found a three-finger tap to work for right-clicking. Neither three nor two for scrolling however.

Touchpad -- Highly sensitive such that when the palm of my hand occasionally touches the touchpad while typing the OS registers it as a single-click. (Happened a few times while typing this post).


Laptop Cooks Itself. -- Anyone know a [smcFanControl](http://www.macupdate.com/info.php/id/23049) equivalent for Linux and/or Windows?! Blame rests squarely on Apple's shoulders. Either open up the firmware, or do a proper job (open preferred lol).

DrCR

____________________
[SIZE="2"]MacBook Pro Santa Rosa, 2.2GHz, 250GB Scorpio, Ceramique compound
Pending: Tux Logo mod
OSX, WinXP, Vista (MSDN), Vector 5.8 SOHO, Sidux 2007-03
Pending Fusion "bootcamps" pointing to native OS installs[/SIZE]

---

### Post by bakert on 2007-10-20
Three-button tap and two-finder scroll and similar can be controlled in xorg.conf.

I currently have:

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "MaxTapTime" "150"
        Option "MaxTapMove" "220"
        Option "MaxDoubleTapTime" "180"
        Option "LockedDrags" "on"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "0"
        Option "TapButton1" "0"
        Option "TapButton2" "0"
        Option "TapButton3" "0"
        Option "Emulate3Buttons" "false"
EndSection

which gives me a nice two-finger scroll but no right-click!

Bear in mind also that these settings interact with those found under Preference, Mouse and that you need to restart X to see changes.

---

### Post by maluka on 2007-10-20
> Laptop Cooks Itself. -- Anyone know a smcFanControl equivalent for Linux and/or Windows?! Blame rests squarely on Apple's shoulders. Either open up the firmware, or do a proper job (open preferred lol).

i have been looking for the same since my second macbook pro battery swoll up and had to be replaced. i have to admit that with gutsy my average operating temperature is much lower than with feisty.

---

### Post by ChardFi on 2007-11-08
Were these issues ever resolved as i'm in the same boat. 

I tried the config i found here [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)  to solve the annoying mouse problem but with no luck. This and the fact i'm paranoid that she's running too hot are my only real problems in life.

Anyone got any further?

---

### Post by graeme77 on 2007-11-14
Hi I read about applesmc but have no idea how to install it, do i need to compile a kernel for it? And SCIM dun seems to be working.. i have the keyboard icon but dun seems to able to select another input method.

---

### Post by cyberdork33 on 2007-11-14
> **graeme77 said:**
> Hi I read about applesmc but have no idea how to install it, do i need to compile a kernel for it? And SCIM dun seems to be working.. i have the keyboard icon but dun seems to able to select another input method.

It is just a kernel module. Load it with:
```
 sudo modprobe applesmc
```

---

### Post by graeme77 on 2007-11-14
thanks, :), keyboard backlight working now.

---

### Post by kervel on 2008-01-02
Hello,

I'm still having trouble to get suspend 2 ram work 100% reliably on gutsy.
things i did:
- compile a fresh kernel to get rid of the gutsy file corruption issues ([https://bugs.launchpad.net/bugs/133786](https://bugs.launchpad.net/bugs/133786)). with a recent release candidate of 2.6.24 there is no more need to patch the kernel for sound (my microphone works too, as does line in), or for the IR remote control (works perfectly)
- got SVN of uvcvideo (no patch needed for isight anymore, only firmware)
- changed /etc/default/acpi-support to blacklist ath_pci and to not save the VBE state and to not POST the video
- disable sync to vblank in compiz

now it already works more reliable than before (i can suspend/resume several times in a row) but when i try 6 times or more, it will fail to resume, or the synaptics device will start going mad (strange mouse movements, no more 2-finger scrolling, no-more right click and so on), or the laptop will start heating up for no reason

madwifi occasionally stops working (suspend->resume solves it) as described here yet, and i also get bitten by [https://bugs.launchpad.net/bugs/124406](https://bugs.launchpad.net/bugs/124406) (keys get "stuck").

other issues i have: when i use nvidia's equivalent of xrandr1.2 , windows maximize accross both screens , but i guess that has nothing to do with mbp

---

