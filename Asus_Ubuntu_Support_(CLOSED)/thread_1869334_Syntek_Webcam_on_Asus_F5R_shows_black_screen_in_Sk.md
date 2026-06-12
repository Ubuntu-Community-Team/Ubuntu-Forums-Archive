---
title: "Syntek Webcam on Asus F5R shows black screen in Skype and Cheese"
date: 2011-10-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dboy4ev on 2011-10-25
I installed Syntek DC-1125 Webcam driver on my Asus F5R. Webcam works very well with Camorama and VLC, but in Skype and in Cheese shows black screen. My Ubuntu is 11.10. When I use Ubuntu 11.04 everything is fine.

---

### Post by dboy4ev on 2011-11-01
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
[COLOR=Red]Bus 001 Device 003: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S[/COLOR]
$ sudo modprobe stk11xx
$ dmesg |tail
dmesg |tail
[  957.937572] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[  957.937575] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A31.
[  957.937578] stk11xx: Release: 0005
[  957.937581] stk11xx: Number of interfaces : 1
[  957.938864] stk11xx: Initialize USB2.0 Syntek Camera
[  958.369341] stk11xx: [COLOR=Red]Check device return error (0x0201 = 0C) ![/COLOR]
[  958.591873] stk11xx: Syntek USB2.0 Camera is ready
[  958.592501] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[  958.593554] usbcore: registered new interface driver usb_stk11xx_driver
[  958.593564] stk11xx: v2.2.0 : Syntek USB Video Camera

$ skype
(skype:4730): Gtk-WARNING **: &#1058;&#1077;&#1084;&#1072;&#1090;&#1072; &#1085;&#1077; &#1084;&#1086;&#1078;&#1077; &#1076;&#1072; &#1073;&#1098;&#1076;&#1077; &#1086;&#1090;&#1082;&#1088;&#1080;&#1090;&#1072; &#1074; &#1087;&#1098;&#1090;&#1103; &#1089; &#1084;&#1086;&#1076;&#1091;&#1083;&#1080;: „pixmap“,

(skype:4730): Gtk-WARNING **: &#1058;&#1077;&#1084;&#1072;&#1090;&#1072; &#1085;&#1077; &#1084;&#1086;&#1078;&#1077; &#1076;&#1072; &#1073;&#1098;&#1076;&#1077; &#1086;&#1090;&#1082;&#1088;&#1080;&#1090;&#1072; &#1074; &#1087;&#1098;&#1090;&#1103; &#1089; &#1084;&#1086;&#1076;&#1091;&#1083;&#1080;: „pixmap“,

(skype:4730): Gtk-WARNING **: &#1058;&#1077;&#1084;&#1072;&#1090;&#1072; &#1085;&#1077; &#1084;&#1086;&#1078;&#1077; &#1076;&#1072; &#1073;&#1098;&#1076;&#1077; &#1086;&#1090;&#1082;&#1088;&#1080;&#1090;&#1072; &#1074; &#1087;&#1098;&#1090;&#1103; &#1089; &#1084;&#1086;&#1076;&#1091;&#1083;&#1080;: „pixmap“,

(skype:4730): Gtk-WARNING **: &#1058;&#1077;&#1084;&#1072;&#1090;&#1072; &#1085;&#1077; &#1084;&#1086;&#1078;&#1077; &#1076;&#1072; &#1073;&#1098;&#1076;&#1077; &#1086;&#1090;&#1082;&#1088;&#1080;&#1090;&#1072; &#1074; &#1087;&#1098;&#1090;&#1103; &#1089; &#1084;&#1086;&#1076;&#1091;&#1083;&#1080;: „pixmap“,

$ dmesg |tail
[  957.937575] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0x6A31.
[  957.937578] stk11xx: Release: 0005
[  957.937581] stk11xx: Number of interfaces : 1
[  957.938864] stk11xx: Initialize USB2.0 Syntek Camera
[  958.369341] stk11xx: [COLOR=Red]Check device return error (0x0201 = 0C) ![/COLOR]
[  958.591873] stk11xx: Syntek USB2.0 Camera is ready
[  958.592501] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[  958.593554] usbcore: registered new interface driver usb_stk11xx_driver
[  958.593564] stk11xx: v2.2.0 : Syntek USB Video Camera
[[COLOR=Red] 1233.495694] process `skype' is using obsolete setsockopt SO_BSDCOMPAT[/COLOR]
cheese

(cheese:5051): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:5051): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:5051): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:5051): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:5051): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:5051): Gtk-WARNING **: Attempting to add a widget with type GtkHBox to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:5051): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:5051): GStreamer-CRITICAL **: gst_value_set_fraction: assertion `denominator != 0' failed

(cheese:5051): GStreamer-CRITICAL **: gst_value_set_fraction: assertion `denominator != 0' failed

** (cheese:5051): WARNING **: ffmpegcsp0: size 921600 is not a multiple of unit size 1228800

** (cheese:5051): WARNING **: &#1042;&#1098;&#1090;&#1088;&#1077;&#1096;&#1085;&#1072; &#1075;&#1088;&#1077;&#1096;&#1082;&#1072; &#1085;&#1072; &#1087;&#1086;&#1090;&#1086;&#1082;&#1072; &#1086;&#1090; &#1076;&#1072;&#1085;&#1085;&#1080;.
$ dmesg |tail
[  957.937578] stk11xx: Release: 0005
[  957.937581] stk11xx: Number of interfaces : 1
[  957.938864] stk11xx: Initialize USB2.0 Syntek Camera
[  958.369341] stk11xx: [COLOR=Red]Check device return error (0x0201 = 0C) ![/COLOR]
[  958.591873] stk11xx: Syntek USB2.0 Camera is ready
[  958.592501] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[  958.593554] usbcore: registered new interface driver usb_stk11xx_driver
[  958.593564] stk11xx: v2.2.0 : Syntek USB Video Camera
[[COLOR=Red] 1233.495694] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1419.101067] stk11xx: Error : Register 0x0001 = 02[/COLOR]

I try:
    $ LD_PRELOAD /usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
Nothing changed.

$ dmesg |tail
[  957.937578] stk11xx: Release: 0005
[  957.937581] stk11xx: Number of interfaces : 1
[  957.938864] stk11xx: Initialize USB2.0 Syntek Camera
[  958.369341] stk11xx:[COLOR=Red] Check device return error (0x0201 = 0C) ![/COLOR]
[  958.591873] stk11xx: Syntek USB2.0 Camera is ready
[  958.592501] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[  958.593554] usbcore: registered new interface driver usb_stk11xx_driver
[  958.593564] stk11xx: v2.2.0 : Syntek USB Video Camera
[ 1233.495694] [COLOR=Red]process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1419.101067] stk11xx: Error : Register 0x0001 = 02[/COLOR]

---

