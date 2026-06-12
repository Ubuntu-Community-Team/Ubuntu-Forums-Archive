---
title: "MBP Pentryn on Ubuntu 8.10 daily"
date: 2008-08-29
forum: Apple Hardware Users
---

### Post by e-gandalf on 2008-08-29
Hi all!

I took the step and installed daily on Penryn.

Results so far:

1) Fast. Really fast comparing 8.04 (eps. booting)
2) The bcm5974 driver is in 2.6.27 kernel so it should give us touchpad out of the box.... but it's not working. I reported it in this thread: [http://ubuntuforums.org/showthread.php?t=840040&page=21](http://ubuntuforums.org/showthread.php?t=840040&page=21)
3) Wifi. Didn't try yet. The open source driver is blocked by lack of N support in b43, but patch for N support is already in the review, so we should have open source driver soon. For now I'll install ndiswrapper probably.
4) Pommed doesn't work. Installed, runned, nothing. :/
5) Sound. Doesn't work out of the box. Tried instructions from Ubuntu Wiki page, but still nothing.

I'll report progress!

---

### Post by cyberdork33 on 2008-08-29
You should especially check these bugs:
[https://bugs.edge.launchpad.net/mactel-support/+bugs](https://bugs.edge.launchpad.net/mactel-support/+bugs)

They are calling for help in determining which bugs need to stay active with the new release.

---

### Post by e-gandalf on 2008-08-29
I saw this, but it doesn't look like what I experience...

More notes:

1) Jockey-gtk crashes
2) Nvidia 177 driver works, but makes compiz not redraw window content so when you load new page, or change tab in window, the content is not redrawn
3) Suspend to ram works perfect
4) Failed to setup apple mouse via bluetooth using default GUI

---

### Post by e-gandalf on 2008-08-30
After today's update sound started working

---

### Post by e-gandalf on 2008-08-30
to launch pommed, you have to modprobe applesmc (it doesn't happen by default).

Despite, changing the backlight or keyboard backlight doesn't work. Sound keys works and eject works.

I'm still fighting with bcm5974 not working and in result lack of touchpad, and with nvidia+compiz making windows not redraw.

---

### Post by e-gandalf on 2008-08-30
hibernation doesn't work.

---

### Post by kosumi68 on 2008-08-31
> **e-gandalf said:**
> to launch pommed, you have to modprobe applesmc (it doesn't happen by default).

Despite, changing the backlight or keyboard backlight doesn't work. Sound keys works and eject works.

I'm still fighting with bcm5974 not working and in result lack of touchpad, and with nvidia+compiz making windows not redraw.

With a proper synaptics driver configuration, the bcm5974 trackpad is working fine. I simply copied the /etc/X11/xorg.conf from my existing hardy installation. Please check the bcm5974 thread for more details.

---

### Post by e-gandalf on 2008-09-09
Another update.

Thanks to kosumi I managed to solve my touchpad problem.
I configured my xorg.conf by hand in the way presented here: [http://rafb.net/p/CNEh8s88.html](http://rafb.net/p/CNEh8s88.html) and the entry about synaptics using /dev/input/mice is solving problem, but with this config, I don't have two-fingers as a right-click not sure why.


The window content is still not being repainted properly with nvidia 177 and compiz.

Additionally, I followed Ubuntu wiki and decided to try to use xcalib ([https://help.ubuntu.com/community/MacBookPro#Screen%20Colors](https://help.ubuntu.com/community/MacBookPro#Screen%20Colors)) but the result colors are (imho) much worse than the default ones shifted into brown/yellow palette.

I'm using Dusk theme ([https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme)) and with the gdm theme from Willbex ([http://danrabbit.deviantart.com/art/Willwill-s-Intrepid-GDM-94051500](http://danrabbit.deviantart.com/art/Willwill-s-Intrepid-GDM-94051500)). It works smooth and nice.

Regarding wireless I had to use ndiswrapper and the instructions from the wiki (the native b43 driver is just getting support for N flavor, but the driver will not exist for much longer). Additionally I had to write a short init script to:
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb

I'm sure there has to be an easier way...

My biggest problem now is pommed not working. Sound works, eject CD works, but no backlight or brightness control :(

---

### Post by hajk on 2008-09-09
I wonder what'll happen with the Broadcom *wl* wireless driver that works fine on my MBP 4,1 (Penryn) with Hardy. Will it be included in the "restricted" modules for 8.10 (since it uses a binary blob)? Has it already been included?

---

### Post by cyberdork33 on 2008-09-09
> **hajk said:**
> I wonder what'll happen with the Broadcom *wl* wireless driver that works fine on my MBP 4,1 (Penryn) with Hardy. Will it be included in the "restricted" modules for 8.10 (since it uses a binary blob)? Has it already been included?
I can check on this tonight since I have a full Intrepid system sunning now. I don't think it is there though...

---

### Post by kosumi68 on 2008-09-17
e-gandalf,

I have been looking into the applesmc problem, and the solution is very close now. I would be very interested in two things from you, since you have the MPP 4,1:

* All the problems reported for applesmc in dmesg:
```

dmesg | grep applesmc | sort -u

```

* The output of the attached script, run as root.

Cheers,
Henrik

---

### Post by kosumi68 on 2008-09-21
I just switched from Hardy to Intrepid, installing Intrepid fresh from the daily live CD. I am running on an MBA, but the experience is very similar to the MPB4,1, so I thought I'd report here anyways. These are my observations:

* CPU and ACPI: works fine

* DISK: works fine, parallel SATA

* WLAN: wl driver works, with two lines in rc.local:
```

rmmod ssb
modprobe wl

```

* LAN: works, using asix driver

* Video: works, with direct rendering

* Sound: works after adding this line to /etc/modprobe.d/alsa-base:
```

options snd_hda_intel model=mbp3

```

* iSight: works, using uvcvideo driver

* Sensors: works, using applesmc with patches from this thread: [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

* Touchpad: works fine

* USB memory stick: works fine

* USB mouse: works fine

* Laptop mode: works after modifying /etc/default/acpi-support

* Screen backlight buttons: Unreliable, strange delays, not using pommed

* Volume buttons: Unreliable, strange delays, not using pommed

* Keyboard backlight buttons: Not working, although manual setting via /sys/class/leds/ works

* Suspend: Unreliable, with strange keyboard problems

* Built-in microphone: Not working

The Bluetooth and IR remote has not been tested, although those are presumably working according to other reports.

Compared to the reports from e-gandalf, this report states that wlan works nicely, that suspend to ram is unreliable, and that there is an additional problem with delayed keyboard echoing in xterm command-line windows. The problem with keyboard backlight is confirmed; there seems to be something handling all such events, but ignoring some of them.

PS: on the fun side, playing neverball (available in package manager) by balancing the laptop in my hands now works :-)

---

### Post by cyberdork33 on 2008-09-21
> **kosumi68 said:**
> I just switched from Hardy to Intrepid, installing Intrepid fresh from the daily live CD. I am running on an MBA, but the experience is very similar to the MPB4,1, so I thought I'd report here anyways. 
Could you check over the MBA wiki page and make any adjustments if needed? I think that the iSight stuff is a bit different than in Hardy for everyone... so I might try to build a new how to for that...

[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

---

### Post by mahatmah on 2008-09-23
I got my Macbook Pro 4.1 last week, but as a Linux user for many years I switched to Intrepid yesterday. 

* Screen/Keyboard backlight buttons: with pommed installed this works when switched to a non-graphical terminal (ctrl+alt+F2). Then switching back to X11. Doesn't work within X11 directly.

* Desktop effects: Works, after installing nvidia drivers trough synaptic. nvidia-xconfig enables driver. Installation trough Hardware Drivers doesn't work.

---

### Post by mahatmah on 2008-09-24
since today the proprietary driver management is working. wl driver for wireless is installed, but networkmanager doesn't recognize my wifi

---

### Post by kjano on 2008-10-04
> **e-gandalf said:**
> 
My biggest problem now is pommed not working. Sound works, eject CD works, but no backlight or brightness control :(

same for me, i just switched to intrepid (running on a santa rosa macbook pro.).

---

### Post by kosumi68 on 2008-10-04
> **kjano said:**
> same for me, i just switched to intrepid (running on a santa rosa macbook pro.).

There is a bug in launchpad reflecting this problem: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894). Upstream [http://bugs.freedesktop.org/show_bug.cgi?id=15844](http://bugs.freedesktop.org/show_bug.cgi?id=15844) claims to have fixed the problem. If it does not, please add comments and/or open a new bug. I do not think the fixes work for MBP4,1.

---

### Post by kosumi68 on 2008-10-04
> **cyberdork33 said:**
> Could you check over the MBA wiki page and make any adjustments if needed? I think that the iSight stuff is a bit different than in Hardy for everyone... so I might try to build a new how to for that...

[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

Perhaps we should split all the wiki pages not only by model but by ubuntu version? I feel the pages gets cluttered with irrelevant information, and the older page, which is still relevant, loses some of its clarity. Besides, the installation in Intrepid is simpler for almost all machines, and it is easier to convince people that it is indeed the case if the wiki page is... simpler :-)

---

### Post by cyberdork33 on 2008-10-04
> **kosumi68 said:**
> Perhaps we should split all the wiki pages not only by model but by ubuntu version? I feel the pages gets cluttered with irrelevant information, and the older page, which is still relevant, loses some of its clarity. Besides, the installation in Intrepid is simpler for almost all machines, and it is easier to convince people that it is indeed the case if the wiki page is... simpler :-)

but having multiple pages for each hardware is also confusing... but I understand what you are saying... I have also thought that the best thing to do would be to split them up according to the specific hardware.... Wifi, iSight, Touchpad, Installation, etc since most of this is common to all Macs with the same hardware.

Just make a replacement section for what exists, and if totally irrelevant, then delete the old, otherwise just make an "archive information" section at the bottom with old data... The great thing about a wiki is even if it is deleted, someone can always come back and get the old revision's text if needed.

---

### Post by kosumi68 on 2008-10-05
> **cyberdork33 said:**
> but having multiple pages for each hardware is also confusing... but I understand what you are saying... I have also thought that the best thing to do would be to split them up according to the specific hardware.... Wifi, iSight, Touchpad, Installation, etc since most of this is common to all Macs with the same hardware.


That sounds really good. If we break down the procedure to configure a particular component of the machine on a particular ubuntu version, we ought to get a handful of different procedures for each. If the same procedure applies to both hardy and intrepid for instance, we link to the same page.

> 
Just make a replacement section for what exists, and if totally irrelevant, then delete the old, otherwise just make an "archive information" section at the bottom with old data... The great thing about a wiki is even if it is deleted, someone can always come back and get the old revision's text if needed.

I think it would be good to keep at least the latest stable version alive along with the development version, since it targets two different uses of ubuntu:

* Install the latest stable version, read the wiki, be done

* Install the development version, read the wiki, contribute

Once the development cycle starts over, one can simply copy the development version over to the stable version.

---

### Post by kosumi68 on 2008-10-05
Ok, I have updated the wiki for MacBook Air, with a proposed structure based at [https://help.ubuntu.com/community/MacBook Models](https://help.ubuntu.com/community/MacBook Models). It seems easiest to be as specific as possible, but trying to break out as many common instructions as possible. Something to go for?

---

### Post by cyberdork33 on 2008-10-05
> **kosumi68 said:**
> I think it would be good to keep at least the latest stable version alive along with the development version, since it targets two different uses of ubuntu:

* Install the latest stable version, read the wiki, be done

* Install the development version, read the wiki, contribute

Once the development cycle starts over, one can simply copy the development version over to the stable version.
Yea that sounds good. I was thinking down the same path as you. Maybe we should also make a wiki page for mactel-support that outlines the general guidelines for all this, and maybe have pointers to current pages, and indicate where needs are. OK OT...

---

### Post by _mario_ on 2008-10-07
Hi all,

yesterday I upgraded my Hardy to Intrepid and wish to give a status report here for the MacBookPro 4 as kosumi68 did for the MacBook Air:

* CPU and ACPI: works
* DISK: works

* WLAN: same as on hardy: wl driver works, with ssb blacklisted. However the wl driver is still freezing the machine when connecting to a WPA2/Enterprise network (WPA2/AES-CCMP via EAP/TTLS). Ndiswrapper works then but has worse link quality. In addition ndiswrapper cannot connect to some access points. wl works then.

* LAN: works
* Video: works

* Sensors: Do not work with the default driver in 2.6.27-5-generic. However compiling the module manually using applesmc with patches from [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) works.

* Sound: works after adding this option in /etc/modprobe.d/:
```
options snd_hda_intel model=mbp3
```

* Built-in microphone: Not tested
* Touchpad: works
* iSight: works
* USB: works
* Bluetooth: works
* IR: works
* Suspend: works. Suspend to RAM did already work in Hardy. Suspend to disk (hibernation) now works in Intrepid using default config files. I cannot tell whether it is really reliable. We'll see soon.

And now for the fun part: function keys and screen/keyboard backlight.

1.) The media player and volume control buttons (from F7 to the right) work. Keyboard and screen backlight do not work in X, although it does work on a text console. Thus, at least the kernel emits a key code. Using xev we can see an event emitted for those keys that is probably never handled. Afaik it is not pommed that handles the volume or eject buttons under X. Looking into the X log shows (shortend):
```

...
(II) evaluating device (MacKeyboard)
(II) XINPUT: Adding extended input device "MacKeyboard" (type: KEYBOARD)
(II) evaluating device (Touchpad)
(II) XINPUT: Adding extended input device "Touchpad" (type: TOUCHPAD)
(II) evaluating device (Mouse)
(II) XINPUT: Adding extended input device "Mouse" (type: MOUSE)
...
(II) config/hal: Adding input device Apple, Inc. Apple Internal Keyboard / Trackpad
(II) LoadModule: "evdev"
(II) XINPUT: Adding extended input device "Apple, Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD)
(II) config/hal: Adding input device Video Bus
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(II) config/hal: Adding input device applesmc
(**) applesmc: always reports core events
(**) applesmc: Device: "/dev/input/event11"
(II) applesmc: Found x and y absolute axes
(WW) applesmc: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "applesmc"
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)

```
The first part are my input devices configured manually. Then Xorg loads the evdev module and configures all devices again (which causes my keyboard AutoRepeat option to also be ignored). Due to this mechanism we can write really short configs now. 

2.) If we remove (rename) the evdev driver in /usr/lib/xorg/module/input/ and restart X, the screen and keyboard backlight buttons work due to pommed, but the media player and volume control buttons do not work anymore. The X server reports a keycode for them with no Symbol attached. This symbol can be defined via xmodmap to get them to work again. In a file .xmodmaprc in the user's home directory define:
```

keycode 144 = XF86Back
keycode 162 = XF86AudioPause
keycode 153 = XF86Forward
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 204 = XF86Eject

```
(German keyboard layout assumed. Check the key codes with xev.)
This is a work-around for now and this nice window showing the current volume level is missing.

> **kosumi68 said:**
> 
PS: on the fun side, playing neverball (available in package manager) by balancing the laptop in my hands now works :-)


great. I really like this game.

Some notes on Intrepid:
* usplash sometimes screws up the screen with nice little arbitrarily colored vertical lines on white/grey ground.
* Switching from X to a text console immediately switches back. Trying again, it works.
* The new human-theme conflicts with gtk2-engine-ubuntulooks. Why? Is it really necessary?

But after all, Intrepid seems to be a better choice than Hardy. Thanks Ubuntu.

ciao,
Mario

---

### Post by _mario_ on 2008-10-07
> **_mario_ said:**
> 
2.) If we remove (rename) the evdev driver in /usr/lib/xorg/module/input/ and restart X, the screen and keyboard backlight buttons work due to pommed, but the media player and volume control buttons do not work anymore.
Adding this to /etc/X11/xorg.conf also prevents the server from querying devices via hal:
```

Section "ServerFlags"
    Option "AutoAddDevices" "off"
EndSection

```
However, working evdev support would be much better.

ciao,
Mario

---

### Post by cyberdork33 on 2008-10-07
> **_mario_ said:**
> And now for the fun part: function keys and screen/keyboard backlight.

1.) The media player and volume control buttons (from F7 to the right) work. Keyboard and screen backlight do not work in X, although it does work on a text console. Thus, at least the kernel emits a key code. Using xev we can see an event emitted for those keys that is probably never handled. Afaik it is not pommed that handles the volume or eject buttons under X. Looking into the X log shows (shortend):
```

...
(II) evaluating device (MacKeyboard)
(II) XINPUT: Adding extended input device "MacKeyboard" (type: KEYBOARD)
(II) evaluating device (Touchpad)
(II) XINPUT: Adding extended input device "Touchpad" (type: TOUCHPAD)
(II) evaluating device (Mouse)
(II) XINPUT: Adding extended input device "Mouse" (type: MOUSE)
...
(II) config/hal: Adding input device Apple, Inc. Apple Internal Keyboard / Trackpad
(II) LoadModule: "evdev"
(II) XINPUT: Adding extended input device "Apple, Inc. Apple Internal Keyboard / Trackpad" (type: KEYBOARD)
(II) config/hal: Adding input device Video Bus
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(II) config/hal: Adding input device applesmc
(**) applesmc: always reports core events
(**) applesmc: Device: "/dev/input/event11"
(II) applesmc: Found x and y absolute axes
(WW) applesmc: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "applesmc"
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)

```The first part are my input devices configured manually. Then Xorg loads the evdev module and configures all devices again (which causes my keyboard AutoRepeat option to also be ignored). Due to this mechanism we can write really short configs now. 

2.) If we remove (rename) the evdev driver in /usr/lib/xorg/module/input/ and restart X, the screen and keyboard backlight buttons work due to pommed, but the media player and volume control buttons do not work anymore. The X server reports a keycode for them with no Symbol attached. This symbol can be defined via xmodmap to get them to work again. In a file .xmodmaprc in the user's home directory define:
```

keycode 144 = XF86Back
keycode 162 = XF86AudioPause
keycode 153 = XF86Forward
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 204 = XF86Eject

```(German keyboard layout assumed. Check the key codes with xev.)
This is a work-around for now and this nice window showing the current volume level is missing.Just a thought, are we sure that it is Xorg killing this functionality? Or maybe it is gnome / Your DE? Have you tried the funtions in a non-Gnome X session?



> **_mario_ said:**
> * usplash sometimes screws up the screen with nice little arbitrarily colored vertical lines on white/grey ground.I have always noticed strange behavior in usplash before final release. I think it is just one of the last things they work on. Priorities...

---

### Post by _mario_ on 2008-10-07
> **cyberdork33 said:**
> Just a thought, are we sure that it is Xorg killing this functionality? Or maybe it is gnome / Your DE? Have you tried the funtions in a non-Gnome X session?
Yes. It is Gnome that makes those media and volume buttons work by interpreting their key syms properly. Unfortunately, the evdev driver emits other key codes (for which key syms exist in the keymap) than the (old?) keyboard driver (for which no key syms exist). The effect remains the same if using another window manager (tested with WindowMaker).

ciao,
Mario

---

### Post by kosumi68 on 2008-10-08
> **_mario_ said:**
> 
And now for the fun part: function keys and screen/keyboard backlight.

1.) The media player and volume control buttons (from F7 to the right) work. Keyboard and screen backlight do not work in X, although it does work on a text console. Thus, at least the kernel emits a key code.


I think both these bugs are relevant:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894)

Regarding lcd backlight, MBP31 and later will possibly be controllable via sysfs and the generic-backlight addon coming in the next HAL version

Regarding kbd backlight, I just submitted a set of patches to fix it work MBP31, MBP41, and MBA, using a new generic-kbd-backlight addon and a simple fdi configuration.

Pommed will not be needed once those hal changes take effect.

---

### Post by kosumi68 on 2008-10-09
> **_mario_ said:**
> 
* Sensors: Do not work with the default driver in 2.6.27-5-generic. However compiling the module manually using applesmc with patches from [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) works.


Applesmc will be fully up to speed in the next Intrepid kernel version (>= 2.6.27-6.9-20).

---

### Post by cyberdork33 on 2008-10-10
> **cyberdork33 said:**
> I can check on this tonight since I have a full Intrepid system sunning now. I don't think it is there though...
Following up on this, on the Beta LiveCD, wl was included on the disc. I still had to rmmod the other broadcom drivers and ssb, then reload wl but it worked. This is great news for Broadcom WiFi users.

---

### Post by Nate53085 on 2008-10-10
Did any of you have trouble with mulitouch?

I have not done any edits to my xorg.conf.

It works sometimes, seems like every other reboot, but thats anecdotal (I don't know for sure)

---

### Post by cyberdork33 on 2008-10-10
> **Nate53085 said:**
> It works sometimes, seems like every other reboot, but thats anecdotal (I don't know for sure)
Please check this thread, and add any information you might have:
[http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040)

---

