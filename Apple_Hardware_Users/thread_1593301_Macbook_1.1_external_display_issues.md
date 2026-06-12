---
title: "Macbook 1.1 external display issues"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by Harkins on 2010-10-11
I have a Macbook 1.1 that's happily run the previous few versions of Ubuntu. I upgraded to Maverick (10.10) last night and can no longer use an external monitor together with my laptop screen for one large desktop.

With no monitor plugged in, the laptop works fine, at its full 1280x800 resolution.

With a monitor plugged in, clicking 'Detect Monitors' in the Monitor control panel (or opening the control panel for the first time, which seems to run the detection) blanks the laptop display. A 1280x800 section of the upper-left of the external monitor displays, and I see the Monitor control panel's 'Hewlett Packard 23"' identification in the upper-left.

The control panel has the correct resolutions for my monitors - 1280x800@60 for the laptop screen, 1920x1200@60 for the external screen, both set to 'On', and the 'Same image in all monitors' checkbox cleared.

If I unplug the external and click 'Detect Monitors' again, the laptop screen works again normally.

Now that xorg.conf is gone, I really have no idea where to start debugging things or what to try. I couldn't turn up any other reports of problems like this with Google. Has anyone seen this problem before, or can suggest suggest any debugging steps?

---

### Post by Harkins on 2010-10-11
A friend suggested I play around with xrandr. -q gives me:
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+1920+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DVI1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 495mm x 310mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1280x1024      85.0     75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       85.0     75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
TV1 disconnected (normal left inverted right x axis y axis)
```

If Screen is the abstracted desktop on top of the hardware, then that's the source of the problem, and would explain why my desktop displays in the upper-left of the external instead of switching modes to 1280x800 on that display.

So I tried to set the Screen size (1900 + 1280 = 3180):
```
$ xrandr --fb 3180x1200
xrandr: specified screen 3180x1200 not large enough for output LVDS1 (1280x800+1920+0)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  33
  Current serial number in output stream:  34
```

I'm still tinkering but wanted to paste this in case anyone recognizes it.

---

### Post by Harkins on 2010-10-11
Well, a bit of progress: it works if I arrange the monitors atop each other but not left/right of each other. So I can use the displays, but not in a way that reflects physical reality.

I'm out of things to try, has anyone seen this before?

(here's what xrandr -q looks like now)
```
Screen 0: minimum 320 x 200, current 1920 x 2000, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+1200 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DVI1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 495mm x 310mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1280x1024      85.0     75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       85.0     75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
TV1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by EvanCarroll on 2010-10-18
I'm having this same problem with an Intel 945GM using the intel driver.

My secondary monitor is
```
  Monitor name: Acer X223W
  Serial No: LDX0D0118512
```

```
$ xrandr --output VGA1 --right-of LVDS1
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  30
  Current serial number in output stream:  31
```

If I set:
```
  SubSection "Display"
          Virtual 2704 1050
  EndSubSection
```

In my xorg.conf, (which I had set in 10.04 to get it to work) I get:

```
  (EE) intel(0): Failed to allocate framebuffer.
```

For completeness here is my `xrandr -q`

```
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA1 connected 1680x1050+1024+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 246mm x 185mm
   1024x768       50.0*+
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)
```

This is already in the bugtracker [619663]("https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/619663"), enabling maverick-proposed and upgrading worked for me.

---

