---
title: "Enabling Auto-Rotation on Toshiba Portege M700 with Mint 12 (Oneiric Ocelot)"
date: 2011-12-26
forum: Any Other OS
---

### Post by Oasu4g on 2011-12-26
Hello everyone,

Happy Holidays. I am starting this thread to hopefully resolve an issue with my Toshiba M700 tablet PC not rotating the screen "out of the box" when I A. Rotate the screen and put my PC into 'tablet mode' or, B. When I rotate the entire computer. Stylus functionality seems to work fine, with the exception of a bug in The Gimp that I also hope to resolve later. I would also like the bezel buttons to work as they did when I had Windows installed on the machine, if that's possible.

A forum goer by the name of Favux here has been kind enough to point me in the right direction regarding my problem. He is one of the maintainers of the Magick Rotation tool available [[COLOR="Red"]here[/COLOR]]("https://launchpad.net/magick-rotation"). I have also browsed over some of his HOWTOs [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1"), which is directed more at people with HP and Dell tablets, but can be repurposed for other models if you know what you're doing. The problem here is, I don't know what I'm doing. I understand somewhat what I need to do, but it's not working after following the simple version of the directions. So I just want to make sure I'm doing the right things here. 

I have the fjbtndrv package installed which can be found [[COLOR="Red"]here[/COLOR]]("https://launchpad.net/~khnz/+archive/ppa?field.series_filter=oneiric"), per Favux's suggestion. I then downloaded and installed the [[COLOR="red"]Magic Rotation[/COLOR]]("https://launchpad.net/magick-rotation") applet and set it up. But, sadly no screen rotation, and the bezel buttons only produce letters, with the exception of a couple, maybe one, which works pretty much how it's supposed to. I think it's the button that brings up the task manager in Windows, and I think it just locks you out of the system under Mint 12. I'll have to use it again to find out, but that is beside the point right now.

I will post the output to lsmod in this post. I don't see anything that suggests that the OS recognizes the tablet 'event' yet, or the accelerometer. It was my understanding that fjbtndrv was the solution to that problem, patching the kernel to detect those functionalities? That was my impression.

What other steps can I take to understand what is going on here? How do I go about troubleshooting this?

Any input would be greatly appreciated. :)

Thank you for your time.

Best regards,

Tim A.

---

### Post by Perfect Storm on 2011-12-26
Moved to Other OS/Distro Talk.

---

### Post by Favux on 2011-12-26
Hi Tim A.,

We seem to have miscommunicated and it is probably my fault.  Since you have  a Toshiba tablet PC the Fujitsu driver fjbtndrv from the PPA will do nothing for you.  That's for Fujitsu tablet PCs.  Instead we need to use something else.  Can you post your output of  *xinput list* entered in a terminal?

I'm not clear what you are saying.  When you say:
> B. When I rotate the entire computer. Stylus functionality seems to work fine,
do you mean when you rotate the screen to inverted?  When it doesn't work are you talking about right or left portrait orientation?

We can look at things a bit and see if there is something Magick Rotation could hook too.

Also we'll have to figure out the bezel buttons ourselves.  How many are there and where are they located on the bezel?  Do you know what function each should have, or what you would like them to have?

Is the bug in Gimp that extra lines are drawn to the left and the top?

---

### Post by Oasu4g on 2011-12-28
Hello Favux,

I'm happy that you're able to take the time to help me out.

Artificial Intelligence,

I apologize for posting in the wrong area. It slipped my mind that Ubuntu has changed so much over the last couple of years. The interfaces are run by different backends now. I didn't think of it until afterward. Thanks for moving it.

Alright, let's see what we're able to accomplish with this. I am attaching the output from 'xinput list' to this post. Maybe you see something of significance here. Following your HOWTO from before, nothing hopeful stood out to me.

The problem with the screen/desktop not rotating, is that it does not rotate automatically, at all. Not when I turn the PC around, or upside down (accelerometer) or in 'tablet mode', where I swivel the screen around on its hinge and fold it down over the keyboard (event originating from a switch in the hinge, I assume).  The stylus, however, works in any state the computer is in, and the 'eraser' as well. Pressure sensitivity and everything. And yes, the bug in The Gimp is where straight lines are automatically drawn straight up and also straight to the left randomly on the image. Very annoying, but I was going to save that for after I got the auto-rotation fixed. Is it connected in some way to the screen rotation? I was curious about that. Regardless I'd love to get that fixed too.

There are five bezel buttons, right below the screen. Seven if you count the power button and the little lock switch for the power button, but I am omitting those in this list.

[LIST]
[*]The first button you can push down, as well as move in four different directions. Originally in Windows, it served the purpose of what would be cursor keys on the keyboard, and an Enter/Return button when pushed down. 

[*]The next one was to trigger screen rotation, in the event you wanted a landscape screen while in 'tablet mode'. Or vice-versa.

[*]The third button works as it's supposed to. It will log you out when pressed, whereas that button brought up a similar screen in Windows. 

[*]The fourth, I believe brought up system information. Not entirely necessary to stick to that, but whatever we're able to do with it, I'll be happy to make it usable. 

[*]The fifth button is designed to cycle between displays, I believe. I haven't tested it under Linux. 
[/LIST]

You can see the buttons (from left to right) in this image at the top:

[IMG]http://www.gottabemobile.com/content/binary/WindowsLiveWriter/HighResShotsoftheToshibaM700TabletPC_9680/IMG_0638.jpg[/IMG]

Right now they type letters or numbers when you press them.

I'll do my best to explain more anything that's left fuzzy.

Thank you very much for your time,


Tim A.

---

### Post by Favux on 2011-12-28
Let's start by fixing Gimp since that is easy.  Gimp is broken for all tablets because of a bug apparently in the Oneiric X stack.  This is probably the same problem that was in Natty but is now worse in Oneiric.  The bug is made obvious by Gimp's history buffer.  See this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  Using Alexia Death's (a Gimp developer) patch to turn of the history buffer Aapo Rantalainen made a PPA of Gimp with the patch and it works.  Just apply the PPA:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)  I'm hoping the Oneiric PPA will also work for Mint 12.


For information on rotation and bezel buttons see the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

Right, so first thing is you need a rotation script.  I'll assume you want to rotate to right handed portrait and use a method 1 script.
```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input tools.

case "$rotation" in
    normal)
    # rotate to the right
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet stylus" rotate  cw
    ;;
    right)
    # rotate to normal
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet stylus" rotate none
    ;;
esac
```
Remember to make it executable.  Now there is one gotcha.  Portrait orientation is broken in Oneiric like it was in Natty.  Oneiric is using xf86-input-wacom-0.11.0.  Although I filed a bug report on that before Oneiric was released and asked them to bump to 0.11.1 which has the bug fix they ignored me.  So you need to update your xf86-input-wacom.  See part II of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") for that.  By the way sample xsetwacom scripts you could probably adapt and use are attached to post #2 there.

Now unfortunately Gnome 3.2 doesn't have launchers anymore by default.  You can install launcher support but you'll need to google that since I've just verified it's there but haven't tried it so I have no instructions yet.  Maybe that is included in one of Mint's extensions?  Looked like a headache.  Anyway I would stick the script in a bin folder/directory you make in /home/yourusername, so /home/yourusername/bin.  You could also and probably should bind the script to your rotate bezel button.

Now one thing.  Is your M700 suppose to have touch?  I thought they had single finger touch but it is not in your *xinput list*.  If your model doesn't have touch or it has two finger touch let me know.

To start looking into to automatic rotation see method 2 and look in the /sys/devices/platform directory.  You're looking for something that says Toshiba acpi or whatever.  Then in there we'd like to find something saying tablet or tablet_mode that changes value say from 0 to 1 when rotated.

For the bezel buttons start looking at appendix 2.  First thing is to enter in a terminal "xev" and when the box pops up press a bezel button and see if you can get the keycodes of all the bezel buttons.  I think you should because in this old laptop wiki for the M700 he was able to use xbindkeys:  [https://wiki.ubuntu.com/SergioZanchetta/Old/ToshibaPortegeM700](https://wiki.ubuntu.com/SergioZanchetta/Old/ToshibaPortegeM700)

---

### Post by Oasu4g on 2012-01-02
The Gimp solution worked perfectly. Thank you for pointing me in the right direction. :D

I am attaching here the output from "ls -anR". Do you see anything that can be used as a "tablet_mode" switch? I think that I came up empty.

**/sys/devices/platform/toshiba_acpi**

```
.:
total 0
drwxr-xr-x  5 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 14 0 0    0 2012-01-02 18:05 ..
drwxr-xr-x  3 0 0    0 2012-01-02 18:05 backlight
drwxr-xr-x  3 0 0    0 2012-01-02 18:05 leds
-r--r--r--  1 0 0 4096 2012-01-02 18:37 modalias
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 power
lrwxrwxrwx  1 0 0    0 2012-01-02 18:05 subsystem -> ../../../bus/platform
-rw-r--r--  1 0 0 4096 2012-01-02 18:05 uevent

./backlight:
total 0
drwxr-xr-x 3 0 0 0 2012-01-02 18:05 .
drwxr-xr-x 5 0 0 0 2012-01-02 18:05 ..
drwxr-xr-x 3 0 0 0 2012-01-02 18:05 toshiba

./backlight/toshiba:
total 0
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 ..
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 actual_brightness
-rw-r--r-- 1 0 0 4096 2012-01-02 18:38 bl_power
-rw-r--r-- 1 0 0 4096 2012-01-02 18:38 brightness
lrwxrwxrwx 1 0 0    0 2012-01-02 18:38 device -> ../../../toshiba_acpi
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 max_brightness
drwxr-xr-x 2 0 0    0 2012-01-02 18:38 power
lrwxrwxrwx 1 0 0    0 2012-01-02 18:05 subsystem -> ../../../../../class/backlight
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 type
-rw-r--r-- 1 0 0 4096 2012-01-02 18:05 uevent

./backlight/toshiba/power:
total 0
drwxr-xr-x 2 0 0    0 2012-01-02 18:38 .
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 ..
-rw-r--r-- 1 0 0 4096 2012-01-02 18:38 async
-rw-r--r-- 1 0 0 4096 2012-01-02 18:38 autosuspend_delay_ms
-rw-r--r-- 1 0 0 4096 2012-01-02 18:38 control
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 runtime_active_kids
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 runtime_active_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 runtime_enabled
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 runtime_status
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 runtime_suspended_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:38 runtime_usage

./leds:
total 0
drwxr-xr-x 3 0 0 0 2012-01-02 18:05 .
drwxr-xr-x 5 0 0 0 2012-01-02 18:05 ..
drwxr-xr-x 3 0 0 0 2012-01-02 18:05 toshiba::illumination

./leds/toshiba::illumination:
total 0
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 ..
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 brightness
lrwxrwxrwx 1 0 0    0 2012-01-02 18:37 device -> ../../../toshiba_acpi
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 max_brightness
drwxr-xr-x 2 0 0    0 2012-01-02 18:37 power
lrwxrwxrwx 1 0 0    0 2012-01-02 18:05 subsystem -> ../../../../../class/leds
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 trigger
-rw-r--r-- 1 0 0 4096 2012-01-02 18:05 uevent

./leds/toshiba::illumination/power:
total 0
drwxr-xr-x 2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 ..
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 async
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 autosuspend_delay_ms
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 control
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_active_kids
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_active_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_enabled
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_status
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_suspended_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_usage

./power:
total 0
drwxr-xr-x 2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 5 0 0    0 2012-01-02 18:05 ..
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 async
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 autosuspend_delay_ms
-rw-r--r-- 1 0 0 4096 2012-01-02 18:37 control
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_active_kids
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_active_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_enabled
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_status
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_suspended_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:37 runtime_usage
```

Next I am going to troubleshoot the bezel buttons. The rotation script is working fine, so I'll try to bind a button to that event.

Thank you very much for your time and help thus far. I really appreciate making this much progress so quickly.

Sincerely,

Tim A.

EDIT: I looked in the "subsystem" linked directory under /sys/devices/platform/toshiba_acpi.

**/sys/devices/platform/toshiba_acpi/susystem**

```
.:
total 0
drwxr-xr-x  4 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 21 0 0    0 2012-01-02 18:05 ..
drwxr-xr-x  2 0 0    0 2012-01-02 18:05 devices
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 drivers
-rw-r--r--  1 0 0 4096 2012-01-02 18:37 drivers_autoprobe
--w-------  1 0 0 4096 2012-01-02 18:37 drivers_probe
--w-------  1 0 0 4096 2012-01-02 18:37 uevent

./devices:
total 0
drwxr-xr-x 2 0 0 0 2012-01-02 18:05 .
drwxr-xr-x 4 0 0 0 2012-01-02 18:05 ..
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 alarmtimer -> ../../../devices/platform/alarmtimer
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 coretemp.0 -> ../../../devices/platform/coretemp.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 dock.0 -> ../../../devices/platform/dock.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 dock.1 -> ../../../devices/platform/dock.1
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 Fixed MDIO bus.0 -> ../../../devices/platform/Fixed MDIO bus.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 i8042 -> ../../../devices/platform/i8042
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 pcspkr -> ../../../devices/platform/pcspkr
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 reg-dummy -> ../../../devices/platform/reg-dummy
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 regulatory.0 -> ../../../devices/platform/regulatory.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 serial8250 -> ../../../devices/platform/serial8250
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 toshiba_acpi -> ../../../devices/platform/toshiba_acpi

./drivers:
total 0
drwxr-xr-x 18 0 0 0 2012-01-02 18:05 .
drwxr-xr-x  4 0 0 0 2012-01-02 18:05 ..
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 88pm860x-regulator
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 ab8500-debug
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 ab8500-gpadc
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 ab8500-regulator
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 ab8500-sysctrl
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 alarmtimer
drwxr-xr-x  2 0 0 0 2012-01-02 18:05 coretemp
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 dsa
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 i8042
drwxr-xr-x  2 0 0 0 2012-01-02 18:05 parport_pc
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 serial8250
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 stmpe-gpio
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 tc3589x-gpio
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 timb-gpio
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 ucb1400_gpio
drwxr-xr-x  2 0 0 0 2012-01-02 18:37 wp_gpio

./drivers/88pm860x-regulator:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/ab8500-debug:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/ab8500-gpadc:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/ab8500-regulator:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/ab8500-sysctrl:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/alarmtimer:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
lrwxrwxrwx  1 0 0    0 2012-01-02 18:38 alarmtimer -> ../../../../devices/platform/alarmtimer
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/coretemp:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
lrwxrwxrwx  1 0 0    0 2012-01-02 18:38 coretemp.0 -> ../../../../devices/platform/coretemp.0
lrwxrwxrwx  1 0 0    0 2012-01-02 18:38 module -> ../../../../module/coretemp
--w-------  1 0 0 4096 2012-01-02 18:05 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/dsa:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/i8042:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
lrwxrwxrwx  1 0 0    0 2012-01-02 18:38 i8042 -> ../../../../devices/platform/i8042
--w-------  1 0 0 4096 2012-01-02 18:38 uevent

./drivers/parport_pc:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
lrwxrwxrwx  1 0 0    0 2012-01-02 18:38 module -> ../../../../module/parport_pc
--w-------  1 0 0 4096 2012-01-02 18:05 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/serial8250:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
lrwxrwxrwx  1 0 0    0 2012-01-02 18:38 serial8250 -> ../../../../devices/platform/serial8250
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/stmpe-gpio:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/tc3589x-gpio:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/timb-gpio:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/ucb1400_gpio:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind

./drivers/wp_gpio:
total 0
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 18 0 0    0 2012-01-02 18:05 ..
--w-------  1 0 0 4096 2012-01-02 18:38 bind
--w-------  1 0 0 4096 2012-01-02 18:38 uevent
--w-------  1 0 0 4096 2012-01-02 18:38 unbind
```

Also, the output under /sys/devices/platform looks interesting. Since toshiba_acpi links back to its parent directory through the subsystem/devices linked directory, is it possible dock.0 and dock.1 are what we're looking for?

If I'm not being clear enough I can explain better.

**/sys/devices/platform** linked back from **/sys/devices/platform/toshiba_acpi** through **/sys/devices/platform/toshiba_acpi/subsystems/devices**

```
.:
total 0
drwxr-xr-x 2 0 0 0 2012-01-02 18:05 .
drwxr-xr-x 4 0 0 0 2012-01-02 18:05 ..
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 alarmtimer -> ../../../devices/platform/alarmtimer
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 coretemp.0 -> ../../../devices/platform/coretemp.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 dock.0 -> ../../../devices/platform/dock.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 dock.1 -> ../../../devices/platform/dock.1
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 Fixed MDIO bus.0 -> ../../../devices/platform/Fixed MDIO bus.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 i8042 -> ../../../devices/platform/i8042
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 pcspkr -> ../../../devices/platform/pcspkr
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 reg-dummy -> ../../../devices/platform/reg-dummy
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 regulatory.0 -> ../../../devices/platform/regulatory.0
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 serial8250 -> ../../../devices/platform/serial8250
lrwxrwxrwx 1 0 0 0 2012-01-02 18:05 toshiba_acpi -> ../../../devices/platform/toshiba_acpi

```

**dock.0**

```
.:
total 0
drwxr-xr-x  3 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 14 0 0    0 2012-01-02 18:05 ..
-r--r--r--  1 0 0 4096 2012-01-02 18:37 docked
-r--r--r--  1 0 0 4096 2012-01-02 18:37 flags
-r--r--r--  1 0 0 4096 2012-01-02 18:37 modalias
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 power
lrwxrwxrwx  1 0 0    0 2012-01-02 18:05 subsystem -> ../../../bus/platform
-r--r--r--  1 0 0 4096 2012-01-02 18:37 type
-rw-r--r--  1 0 0 4096 2012-01-02 18:05 uevent
-r--r--r--  1 0 0 4096 2012-01-02 18:37 uid
--w-------  1 0 0 4096 2012-01-02 18:37 undock

./power:
total 0
drwxr-xr-x 2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 ..
-rw-r--r-- 1 0 0 4096 2012-01-02 18:59 async
-rw-r--r-- 1 0 0 4096 2012-01-02 18:59 autosuspend_delay_ms
-rw-r--r-- 1 0 0 4096 2012-01-02 18:59 control
-r--r--r-- 1 0 0 4096 2012-01-02 18:59 runtime_active_kids
-r--r--r-- 1 0 0 4096 2012-01-02 18:59 runtime_active_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:59 runtime_enabled
-r--r--r-- 1 0 0 4096 2012-01-02 18:59 runtime_status
-r--r--r-- 1 0 0 4096 2012-01-02 18:59 runtime_suspended_time
-r--r--r-- 1 0 0 4096 2012-01-02 18:59 runtime_usage
```

**dock.1**

```
.:
total 0
drwxr-xr-x  3 0 0    0 2012-01-02 18:05 .
drwxr-xr-x 14 0 0    0 2012-01-02 18:05 ..
-r--r--r--  1 0 0 4096 2012-01-02 18:37 docked
-r--r--r--  1 0 0 4096 2012-01-02 18:37 flags
-r--r--r--  1 0 0 4096 2012-01-02 18:37 modalias
drwxr-xr-x  2 0 0    0 2012-01-02 18:37 power
lrwxrwxrwx  1 0 0    0 2012-01-02 18:05 subsystem -> ../../../bus/platform
-r--r--r--  1 0 0 4096 2012-01-02 18:37 type
-rw-r--r--  1 0 0 4096 2012-01-02 18:05 uevent
-r--r--r--  1 0 0 4096 2012-01-02 18:37 uid
--w-------  1 0 0 4096 2012-01-02 18:37 undock

./power:
total 0
drwxr-xr-x 2 0 0    0 2012-01-02 18:37 .
drwxr-xr-x 3 0 0    0 2012-01-02 18:05 ..
-rw-r--r-- 1 0 0 4096 2012-01-02 19:33 async
-rw-r--r-- 1 0 0 4096 2012-01-02 19:33 autosuspend_delay_ms
-rw-r--r-- 1 0 0 4096 2012-01-02 19:33 control
-r--r--r-- 1 0 0 4096 2012-01-02 19:33 runtime_active_kids
-r--r--r-- 1 0 0 4096 2012-01-02 19:33 runtime_active_time
-r--r--r-- 1 0 0 4096 2012-01-02 19:33 runtime_enabled
-r--r--r-- 1 0 0 4096 2012-01-02 19:33 runtime_status
-r--r--r-- 1 0 0 4096 2012-01-02 19:33 runtime_suspended_time
-r--r--r-- 1 0 0 4096 2012-01-02 19:33 runtime_usage
```

---

### Post by Favux on 2012-01-02
> is it possible dock.0 and dock.1 are what we're looking for?
Yes.  Originally the swivel hinge signal was conflated in the dock signal for the hp-wmi.ko until Matthew Garrett separated in out for us in the hp-wmi.c.  So Magick originally started by reading:
```
cat /sys/devices/platform/hp-wmi/dock
```
and it would give 0 for laptop and 1 for tablet mode and the same for dock and undock of course.  You had to use a patched hp-wmi.c for it to read:
```
cat /sys/devices/platform/hp-wmi/tablet
```
until Matthew's (the module maintainer) patch made it into the kernel.

So it is worth looking into.  If I'm following you correctly we want to try:
```
cat /sys/devices/platform/toshiba_acpi/subsystems/devices/dock.0
```
and
```
cat /sys/devices/platform/toshiba_acpi/subsystems/devices/dock.1
```
assuming I have the directory correct.  Run it in laptop, swivel to tablet and run again.  Then run again when back in laptop.  Might we see docked or undock instead of 0 or 1?  Something on one of the docks anyway I hope.

---

### Post by Oasu4g on 2012-01-04
All that it returns is that both dock.0 and dock.1 are directories. I tried both of the cat commands you suggested. Why do you think that it sees them as directories only, and not proper events?

---

### Post by Favux on 2012-01-04
We're looking for a file to cat.  You can use Nautilus (Places) to quickly check that out.

For example when I look in my tablet PC's /sys/devices/platform I see two candidate directories:  dock.0 and hp-wmi, among others.  When I look in /sys/devices/platform/dock.0 I see the files docked and undock.  When I open docked in gedit the value is 1.  It won't let me open undock in gedit telling me I don't have permission.  (So if I want to cat that one I'd try prefacing the command with sudo.  The ones you've listed seem to have read only permissions so you'd be good.)

When I look in /sys/devices/platform/hp-wmi I see the file dock (and of course the file tablet).  When I open dock in gedit I get the value 0.

So use Nautilus and gedit to find candidate files to cat using the directory path to them.  And of course we're looking for the value to change with screen rotation from laptop to tablet modes.

---

