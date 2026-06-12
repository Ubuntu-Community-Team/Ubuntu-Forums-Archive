---
title: "External monitor resolution"
date: 2011-11-23
forum: Apple Hardware Users
---

### Post by DARKAD on 2011-11-23
I got two hard disks for my macbook 4,1.

One has refit + leopard + ubuntustudio10.04 with this kind of installation: [http://www.rodsbooks.com/ubuntu-efi/index.html]("http://www.rodsbooks.com/ubuntu-efi/index.html")

the other has ubuntustudio 11.10 with its automatic installation.

Now on the ubuntu 10.04 I can see the exact resolution 1360x768, while on ubuntu 11.10 I can only see 1024x768 resolution.

Do this happen because the ubuntu 11.10 doesn't read informations from the leopard efi?

---testing---
the xrandr from ubuntu 10.04:
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 8192 x 8192
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1360x768 59.8*
1024x768 60.0
800x600 60.3 56.2
848x480 60.0
640x480 59.9 59.9
LVDS1 connected (normal left inverted right x axis y axis)
1280x800 59.9 +
1024x768 85.0 75.0 70.1 60.0
832x624 74.6
800x600 85.1 72.2 75.0 60.3 56.2
640x480 85.0 72.8 75.0 59.9
720x400 85.0
640x400 85.1
640x350 85.1
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

the xrandr from ubuntu 11.10:
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
1280x800 59.9*+
1024x768 60.0
800x600 60.3 56.2
640x480 59.9
VGA1 connected (normal left inverted right x axis y axis)
1024x768 60.0
800x600 60.3 56.2
848x480 60.0
640x480 59.9
DVI1 unknown connection (normal left inverted right x axis y axis)
1360x768 59.8
1152x864 60.0
1024x768 60.0
800x600 60.3
640x480 59.9
TV1 disconnected (normal left inverted right x axis y axis)

with dmidecode both say:
Handle 0x001D, DMI type 10, 6 bytes
On Board Device Information
Type: Video
Status: Enabled
Description: FIX THIS Graphics Controller

---

### Post by DARKAD on 2011-11-23
Here are the solutions:
[http://myit-solutions.blogspot.com/2010/09/how-to-add-and-set-custom-display.html]("http://myit-solutions.blogspot.com/2010/09/how-to-add-and-set-custom-display.html")

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by DARKAD on 2011-11-23
From console I did:
cvt 1360 768 59.8

xrandr --newmode "1360x768_59.80"   84.50  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

xrandr --addmode VGA1 1360x768_59.80

xrandr --output VGA1 --mode 1360x768_59.80

---

