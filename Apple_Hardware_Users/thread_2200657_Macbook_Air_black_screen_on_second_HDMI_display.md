---
title: "Macbook Air: black screen on second HDMI display"
date: 2014-01-20
forum: Apple Hardware Users
---

### Post by nicolo.p on 2014-01-20
My machine is an Apple Macbook Air 1,1 from Early 2008, and I'm running Ubuntu 12.04 with kernel Linux 3.2.0-58-generic-pae.

When I connect it to an HD TV via the minidisplayport-DVI (Apple adapter) --> DVI-HDMI (cable) I get the TV recognized in System Settings -> Displays, but the TV only gets a completely *black screen* signal (i.e. it gets a signal, because if I unplug the cable or disable the TV screen in Ubuntu the TV then says 'no signal', but this signal is black screen).

The output from xrandr (with cable plugged in) is

    ```

Screen 0: minimum 320 x 200, current 3200 x 1080, maximum 8192 x 8192
LVDS1 connected 1280x800+0+12 (normal left inverted right x axis y axis) 286mm x 179mm
       1280x800       61.2*+
       1024x768       60.0  
       800x600        60.3     56.2  
       640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+1280+0 (normal left inverted right x axis y axis) 1280mm x 720mm
       1920x1080      60.0*+   50.0     24.0  
       1600x1200      60.0  
       1280x1024      60.0  
       1360x768       59.8  
       1024x768       60.0  
       800x600        60.3  
       640x480        60.0  
TV1 unknown connection (normal left inverted right x axis y axis)
       848x480        59.9 +
       640x480        59.9 +
       1024x768       59.9  
       800x600        59.9

```


----------

Am I missing some configuration in Ubuntu? or is that a driver problem for the TV or the Apple adapter? Could it be related to Compiz or nvidia drivers?

---

### Post by xSCCMx on 2014-01-21
Probably nVidia.... (I'm gonna take a blind stab) Does your Mac have intel intergreated graphics?

---

### Post by nicolo.p on 2014-02-11
[FONT=arial][SIZE=2]I'm sorry for the delay in reply
From Apple page I read
[/SIZE][/FONT][h=3][FONT=arial][SIZE=2]Graphics and video support
Intel GMA X3100 graphics processor with 144MB of DDR2 SDRAM shared with main memory
[/SIZE][/FONT][/h][FONT=arial][SIZE=2]Extended desktop and video mirroring: Simultaneously supports full  native resolution on the built-in display and up to 1920 by 1200 pixels  on an external display, both at millions of colors
[/SIZE][/FONT]
[FONT=arial][SIZE=2] [/SIZE][/FONT][FONT=arial][SIZE=2]Built-in iSight camera
[/SIZE][/FONT]
[FONT=arial][SIZE=2] [/SIZE][/FONT][FONT=arial][SIZE=2]Mini-DVI port
[/SIZE][/FONT]

---

### Post by nicolo.p on 2014-02-11
Do you know what I should try?

---

### Post by nicolo.p on 2014-02-11
actually, I'm a bit confused, since I get
```
cat /proc/driver/nvidia/version
No such file or directory
```
so am I not using any nvidia drivers? could installing some (like nvidia-current) help?

---

### Post by bapoumba on 2014-02-11
Moved to Apple Users. Your thread may find more attention from people having installed Ubuntu on their Apple machine here.

---

### Post by nicolo.p on 2014-02-12
OK, hope someone can help

---

### Post by nicolo.p on 2014-02-14
nvidia seems to be ruled out, since with lspci I get
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
any other ideas?

---

### Post by nicolo.p on 2014-02-14
even better
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Apple Inc. Device 00a2
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at 90000000 (64-bit, non-prefetchable) [size=1M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5110 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
    Subsystem: Apple Inc. Device 00a2
    Flags: bus master, fast devsel, latency 0
    Memory at 90100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
```

---

### Post by nicolo.p on 2014-02-14
is it correct to say that with these
```
nicolo@mba:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:90000000-900fffff memory:80000000-8fffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:90100000-901fffff
```
I should not install nvidia drivers?

---

### Post by nicolo.p on 2014-02-14
the tv I link to is philips 32pfl4007m/08

---

### Post by nicolo.p on 2014-02-14
instead in system settings -> displays it gets named philips consumer electronics 58''

---

### Post by nicolo.p on 2014-02-14
both the laptop and tv notice when I plug/unplug the cable

---

