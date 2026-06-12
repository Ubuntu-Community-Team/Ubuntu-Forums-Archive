---
title: "Ati Radeon 9600 and 30&quot; Cinema Display"
date: 2010-11-29
forum: Apple Hardware Users
---

### Post by SP3RRFEUER on 2010-11-29
Hi community,

i'm running Ubuntu 10.10 on a PowerMac G5 with an ATI Radeon 9600 Pro (Dual Link DVI) videocard installed. Is there a way to get the native 2560x1600 resolution for the 30" Cinema Display working?

Thanks in Advance!

---

### Post by linuxopjemac on 2010-11-29
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

and maybe you need a modeline for that resolution.

what is the output of:
```
cvt 2560 1600
```

you could add the output of that line in the Monitor Section of the xorg.conf file.

---

### Post by SP3RRFEUER on 2010-11-29
thanks for the fast reply. since i'm completely new to this could you explain where i have to place this xorg.conf? is it /etc/X11/xorg.conf ?

---

### Post by linuxopjemac on 2010-11-29
> is it /etc/X11/xorg.conf ? 

yes

---

### Post by SP3RRFEUER on 2010-11-29
my screen doesn't work at all after creating this file

---

### Post by linuxopjemac on 2010-11-29
turn off kms, as described at the top of that page, maybe that helps.

---

### Post by SP3RRFEUER on 2010-11-29
> **linuxopjemac said:**
> turn off kms, as described at the top of that page, maybe that helps.

nope screen keeps black as well :-(

---

### Post by linuxopjemac on 2010-11-29
mmm .... I think I know why....

change BusID from "PCI:0:16:0" to "PCI:240:16:0" in the Device Section of xorg.conf.

if that does not solve your problem, paste me the output of:
```
cat /var/log/Xorg.0.log

```

---

### Post by SP3RRFEUER on 2010-11-29
> **linuxopjemac said:**
> mmm .... I think I know why....

change BusID from "PCI:0:16:0" to "PCI:240:16:0" in the Device Section of xorg.conf.

if that does not solve your problem, paste me the output of:
```
cat /var/log/Xorg.0.log

```

the screen works again with the new BusID setting but it still shows me two 1280x800 screens instead of one 2560x1600. I added the following to the xorg.conf file: Option "AllowDualLinkModes" "true" which had no effect either.

Here's the log entry you requested:

11
[   182.370] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   182.370] (II) RADEON(0): Manufacturer's mask: 0
[   182.370] (II) RADEON(0): Supported detailed timing:
[   182.370] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   182.371] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   182.371] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   182.371] (II) RADEON(0): Supported detailed timing:
[   182.371] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   182.371] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   182.371] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   182.371] (II) RADEON(0): Serial No: CY5520D5UG1
[   182.371] (II) RADEON(0): Monitor name: Cinema HD
[   182.371] (II) RADEON(0): Number of EDID sections to follow: 1
[   182.371] (II) RADEON(0): EDID (in hex):
[   182.371] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   182.371] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   182.371] (II) RADEON(0): 	13505400000001010101010101010101
[   182.371] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   182.371] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   182.371] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   182.371] (II) RADEON(0): 	593535323044355547310a00000000fc
[   182.371] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   182.371] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   182.371] (II) RADEON(0): 	031919a8000000000000400000000000
[   182.371] (II) RADEON(0): 	00000000000000000000000000000000
[   182.371] (II) RADEON(0): 	00000000000000000000000000000000
[   182.371] (II) RADEON(0): 	00000000000000000000000000000000
[   182.371] (II) RADEON(0): 	00000000000000000000000000000000
[   182.371] (II) RADEON(0): 	00000000000000000000000000000000
[   182.371] (II) RADEON(0): 	00000000000000000000000000000049
[   182.371] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   182.376] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   182.376] Unhandled monitor type 0
[   182.485] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   182.485] (II) RADEON(0): Printing DDC gathered Modelines:
[   182.485] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   182.485] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   182.485] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   182.485] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   182.485] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   182.485] (II) RADEON(0): Year: 2005  Week: 52
[   182.485] (II) RADEON(0): EDID Version: 1.3
[   182.485] (II) RADEON(0): Digital Display Input
[   182.485] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   182.485] (II) RADEON(0): Gamma: 2.20
[   182.485] (II) RADEON(0): DPMS capabilities: Off
[   182.485] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   182.485] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   182.485] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   182.485] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   182.485] (II) RADEON(0): Manufacturer's mask: 0
[   182.485] (II) RADEON(0): Supported detailed timing:
[   182.485] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   182.485] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   182.486] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   182.486] (II) RADEON(0): Supported detailed timing:
[   182.486] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   182.486] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   182.486] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   182.486] (II) RADEON(0): Serial No: CY5520D5UG1
[   182.486] (II) RADEON(0): Monitor name: Cinema HD
[   182.486] (II) RADEON(0): Number of EDID sections to follow: 1
[   182.486] (II) RADEON(0): EDID (in hex):
[   182.486] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   182.486] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   182.486] (II) RADEON(0): 	13505400000001010101010101010101
[   182.486] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   182.486] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   182.486] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   182.486] (II) RADEON(0): 	593535323044355547310a00000000fc
[   182.486] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   182.486] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   182.486] (II) RADEON(0): 	031919a8000000000000400000000000
[   182.486] (II) RADEON(0): 	00000000000000000000000000000000
[   182.486] (II) RADEON(0): 	00000000000000000000000000000000
[   182.486] (II) RADEON(0): 	00000000000000000000000000000000
[   182.486] (II) RADEON(0): 	00000000000000000000000000000000
[   182.486] (II) RADEON(0): 	00000000000000000000000000000000
[   182.486] (II) RADEON(0): 	00000000000000000000000000000049
[   182.486] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   182.491] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   182.491] Unhandled monitor type 0
[   182.600] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   182.600] (II) RADEON(0): Printing DDC gathered Modelines:
[   182.601] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   182.601] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   182.601] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   182.601] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   182.601] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   182.601] (II) RADEON(0): Year: 2005  Week: 52
[   182.601] (II) RADEON(0): EDID Version: 1.3
[   182.601] (II) RADEON(0): Digital Display Input
[   182.601] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   182.601] (II) RADEON(0): Gamma: 2.20
[   182.601] (II) RADEON(0): DPMS capabilities: Off
[   182.601] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   182.601] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   182.601] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   182.601] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   182.601] (II) RADEON(0): Manufacturer's mask: 0
[   182.601] (II) RADEON(0): Supported detailed timing:
[   182.601] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   182.601] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   182.601] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   182.601] (II) RADEON(0): Supported detailed timing:
[   182.601] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   182.601] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   182.601] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   182.601] (II) RADEON(0): Serial No: CY5520D5UG1
[   182.601] (II) RADEON(0): Monitor name: Cinema HD
[   182.601] (II) RADEON(0): Number of EDID sections to follow: 1
[   182.601] (II) RADEON(0): EDID (in hex):
[   182.601] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   182.601] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   182.601] (II) RADEON(0): 	13505400000001010101010101010101
[   182.601] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   182.601] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   182.601] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   182.602] (II) RADEON(0): 	593535323044355547310a00000000fc
[   182.602] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   182.602] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   182.602] (II) RADEON(0): 	031919a8000000000000400000000000
[   182.602] (II) RADEON(0): 	00000000000000000000000000000000
[   182.602] (II) RADEON(0): 	00000000000000000000000000000000
[   182.602] (II) RADEON(0): 	00000000000000000000000000000000
[   182.602] (II) RADEON(0): 	00000000000000000000000000000000
[   182.602] (II) RADEON(0): 	00000000000000000000000000000000
[   182.602] (II) RADEON(0): 	00000000000000000000000000000049
[   182.602] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   182.606] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   182.606] Unhandled monitor type 0
[   182.714] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   182.715] (II) RADEON(0): Printing DDC gathered Modelines:
[   182.715] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   182.715] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   182.715] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   182.715] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   182.715] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   182.715] (II) RADEON(0): Year: 2005  Week: 52
[   182.715] (II) RADEON(0): EDID Version: 1.3
[   182.715] (II) RADEON(0): Digital Display Input
[   182.715] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   182.715] (II) RADEON(0): Gamma: 2.20
[   182.715] (II) RADEON(0): DPMS capabilities: Off
[   182.715] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   182.715] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   182.715] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   182.715] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   182.715] (II) RADEON(0): Manufacturer's mask: 0
[   182.715] (II) RADEON(0): Supported detailed timing:
[   182.715] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   182.715] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   182.715] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   182.715] (II) RADEON(0): Supported detailed timing:
[   182.715] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   182.715] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   182.715] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   182.715] (II) RADEON(0): Serial No: CY5520D5UG1
[   182.715] (II) RADEON(0): Monitor name: Cinema HD
[   182.715] (II) RADEON(0): Number of EDID sections to follow: 1
[   182.715] (II) RADEON(0): EDID (in hex):
[   182.715] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   182.715] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   182.715] (II) RADEON(0): 	13505400000001010101010101010101
[   182.715] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   182.716] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   182.716] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   182.716] (II) RADEON(0): 	593535323044355547310a00000000fc
[   182.716] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   182.716] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   182.716] (II) RADEON(0): 	031919a8000000000000400000000000
[   182.716] (II) RADEON(0): 	00000000000000000000000000000000
[   182.716] (II) RADEON(0): 	00000000000000000000000000000000
[   182.716] (II) RADEON(0): 	00000000000000000000000000000000
[   182.716] (II) RADEON(0): 	00000000000000000000000000000000
[   182.716] (II) RADEON(0): 	00000000000000000000000000000000
[   182.716] (II) RADEON(0): 	00000000000000000000000000000049
[   182.716] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   182.721] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   182.721] Unhandled monitor type 0
[   191.767] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   191.767] (II) RADEON(0): Printing DDC gathered Modelines:
[   191.767] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   191.767] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   191.767] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   191.767] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   191.767] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   191.768] (II) RADEON(0): Year: 2005  Week: 52
[   191.768] (II) RADEON(0): EDID Version: 1.3
[   191.768] (II) RADEON(0): Digital Display Input
[   191.768] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   191.768] (II) RADEON(0): Gamma: 2.20
[   191.768] (II) RADEON(0): DPMS capabilities: Off
[   191.768] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   191.768] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   191.768] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   191.768] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   191.768] (II) RADEON(0): Manufacturer's mask: 0
[   191.768] (II) RADEON(0): Supported detailed timing:
[   191.768] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   191.768] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   191.768] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   191.768] (II) RADEON(0): Supported detailed timing:
[   191.768] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   191.768] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   191.768] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   191.768] (II) RADEON(0): Serial No: CY5520D5UG1
[   191.768] (II) RADEON(0): Monitor name: Cinema HD
[   191.768] (II) RADEON(0): Number of EDID sections to follow: 1
[   191.768] (II) RADEON(0): EDID (in hex):
[   191.768] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   191.768] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   191.768] (II) RADEON(0): 	13505400000001010101010101010101
[   191.768] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   191.768] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   191.768] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   191.768] (II) RADEON(0): 	593535323044355547310a00000000fc
[   191.768] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   191.768] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   191.768] (II) RADEON(0): 	031919a8000000000000400000000000
[   191.768] (II) RADEON(0): 	00000000000000000000000000000000
[   191.769] (II) RADEON(0): 	00000000000000000000000000000000
[   191.769] (II) RADEON(0): 	00000000000000000000000000000000
[   191.769] (II) RADEON(0): 	00000000000000000000000000000000
[   191.769] (II) RADEON(0): 	00000000000000000000000000000000
[   191.769] (II) RADEON(0): 	00000000000000000000000000000049
[   191.769] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   191.773] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   191.773] Unhandled monitor type 0
[   191.885] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   191.885] (II) RADEON(0): Printing DDC gathered Modelines:
[   191.885] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   191.885] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   191.885] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   191.886] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   191.886] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   191.886] (II) RADEON(0): Year: 2005  Week: 52
[   191.886] (II) RADEON(0): EDID Version: 1.3
[   191.886] (II) RADEON(0): Digital Display Input
[   191.886] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   191.886] (II) RADEON(0): Gamma: 2.20
[   191.886] (II) RADEON(0): DPMS capabilities: Off
[   191.886] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   191.886] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   191.886] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   191.886] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   191.886] (II) RADEON(0): Manufacturer's mask: 0
[   191.886] (II) RADEON(0): Supported detailed timing:
[   191.886] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   191.886] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   191.886] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   191.886] (II) RADEON(0): Supported detailed timing:
[   191.886] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   191.886] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   191.886] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   191.886] (II) RADEON(0): Serial No: CY5520D5UG1
[   191.886] (II) RADEON(0): Monitor name: Cinema HD
[   191.886] (II) RADEON(0): Number of EDID sections to follow: 1
[   191.886] (II) RADEON(0): EDID (in hex):
[   191.886] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   191.886] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   191.886] (II) RADEON(0): 	13505400000001010101010101010101
[   191.886] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   191.886] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   191.886] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   191.886] (II) RADEON(0): 	593535323044355547310a00000000fc
[   191.886] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   191.886] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   191.886] (II) RADEON(0): 	031919a8000000000000400000000000
[   191.887] (II) RADEON(0): 	00000000000000000000000000000000
[   191.887] (II) RADEON(0): 	00000000000000000000000000000000
[   191.887] (II) RADEON(0): 	00000000000000000000000000000000
[   191.887] (II) RADEON(0): 	00000000000000000000000000000000
[   191.887] (II) RADEON(0): 	00000000000000000000000000000000
[   191.887] (II) RADEON(0): 	00000000000000000000000000000049
[   191.887] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   191.891] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   191.891] Unhandled monitor type 0
[   192.001] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   192.001] (II) RADEON(0): Printing DDC gathered Modelines:
[   192.001] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   192.001] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   192.001] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   192.001] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   192.001] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   192.001] (II) RADEON(0): Year: 2005  Week: 52
[   192.001] (II) RADEON(0): EDID Version: 1.3
[   192.001] (II) RADEON(0): Digital Display Input
[   192.001] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   192.001] (II) RADEON(0): Gamma: 2.20
[   192.001] (II) RADEON(0): DPMS capabilities: Off
[   192.001] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   192.001] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   192.001] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   192.001] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   192.002] (II) RADEON(0): Manufacturer's mask: 0
[   192.002] (II) RADEON(0): Supported detailed timing:
[   192.002] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   192.002] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   192.002] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   192.002] (II) RADEON(0): Supported detailed timing:
[   192.002] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   192.002] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   192.002] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   192.002] (II) RADEON(0): Serial No: CY5520D5UG1
[   192.002] (II) RADEON(0): Monitor name: Cinema HD
[   192.002] (II) RADEON(0): Number of EDID sections to follow: 1
[   192.002] (II) RADEON(0): EDID (in hex):
[   192.002] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   192.002] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   192.002] (II) RADEON(0): 	13505400000001010101010101010101
[   192.002] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   192.002] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   192.002] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   192.002] (II) RADEON(0): 	593535323044355547310a00000000fc
[   192.002] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   192.002] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   192.002] (II) RADEON(0): 	031919a8000000000000400000000000
[   192.002] (II) RADEON(0): 	00000000000000000000000000000000
[   192.002] (II) RADEON(0): 	00000000000000000000000000000000
[   192.002] (II) RADEON(0): 	00000000000000000000000000000000
[   192.002] (II) RADEON(0): 	00000000000000000000000000000000
[   192.002] (II) RADEON(0): 	00000000000000000000000000000000
[   192.002] (II) RADEON(0): 	00000000000000000000000000000049
[   192.002] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   192.007] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   192.007] Unhandled monitor type 0
[   204.983] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   204.983] (II) RADEON(0): Printing DDC gathered Modelines:
[   204.983] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   204.983] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   204.983] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   204.983] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   204.983] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   204.983] (II) RADEON(0): Year: 2005  Week: 52
[   204.983] (II) RADEON(0): EDID Version: 1.3
[   204.983] (II) RADEON(0): Digital Display Input
[   204.984] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   204.984] (II) RADEON(0): Gamma: 2.20
[   204.984] (II) RADEON(0): DPMS capabilities: Off
[   204.984] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   204.984] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   204.984] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   204.984] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   204.984] (II) RADEON(0): Manufacturer's mask: 0
[   204.984] (II) RADEON(0): Supported detailed timing:
[   204.984] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   204.984] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   204.984] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   204.984] (II) RADEON(0): Supported detailed timing:
[   204.984] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   204.984] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   204.984] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   204.984] (II) RADEON(0): Serial No: CY5520D5UG1
[   204.984] (II) RADEON(0): Monitor name: Cinema HD
[   204.984] (II) RADEON(0): Number of EDID sections to follow: 1
[   204.984] (II) RADEON(0): EDID (in hex):
[   204.984] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   204.984] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   204.984] (II) RADEON(0): 	13505400000001010101010101010101
[   204.984] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   204.984] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   204.984] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   204.984] (II) RADEON(0): 	593535323044355547310a00000000fc
[   204.984] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   204.984] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   204.984] (II) RADEON(0): 	031919a8000000000000400000000000
[   204.984] (II) RADEON(0): 	00000000000000000000000000000000
[   204.984] (II) RADEON(0): 	00000000000000000000000000000000
[   204.984] (II) RADEON(0): 	00000000000000000000000000000000
[   204.984] (II) RADEON(0): 	00000000000000000000000000000000
[   204.985] (II) RADEON(0): 	00000000000000000000000000000000
[   204.985] (II) RADEON(0): 	00000000000000000000000000000049
[   204.985] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   204.989] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   204.989] Unhandled monitor type 0
[   207.302] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   207.302] (II) RADEON(0): Printing DDC gathered Modelines:
[   207.302] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328
1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   207.302] (II) RADEON(0): Modeline "2560x1600"x0.0  268.00  2560 2608
2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz)
[   207.302] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 3
[   207.302] (II) RADEON(0): EDID data from the display on output: DVI-1
----------------------
[   207.302] (II) RADEON(0): Manufacturer: APP  Model: 9232  Serial#:
33554879
[   207.302] (II) RADEON(0): Year: 2005  Week: 52
[   207.302] (II) RADEON(0): EDID Version: 1.3
[   207.302] (II) RADEON(0): Digital Display Input
[   207.302] (II) RADEON(0): Max Image Size [cm]: horiz.: 64  vert.: 40
[   207.302] (II) RADEON(0): Gamma: 2.20
[   207.302] (II) RADEON(0): DPMS capabilities: Off
[   207.302] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb
4:4:4 
[   207.302] (II) RADEON(0): First detailed timing not preferred mode in
violation of standard!
[   207.302] (II) RADEON(0): redX: 0.640 redY: 0.343   greenX: 0.292
greenY: 0.611
[   207.302] (II) RADEON(0): blueX: 0.146 blueY: 0.074   whiteX: 0.313
whiteY: 0.331
[   207.302] (II) RADEON(0): Manufacturer's mask: 0
[   207.302] (II) RADEON(0): Supported detailed timing:
[   207.302] (II) RADEON(0): clock: 71.0 MHz   Image Size:  641 x 401 mm
[   207.302] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end
1360 h_blank_end 1440 h_border: 0
[   207.302] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809
v_blanking: 823 v_border: 0
[   207.302] (II) RADEON(0): Supported detailed timing:
[   207.302] (II) RADEON(0): clock: 268.0 MHz   Image Size:  641 x 401
mm
[   207.302] (II) RADEON(0): h_active: 2560  h_sync: 2608  h_sync_end
2640 h_blank_end 2720 h_border: 0
[   207.302] (II) RADEON(0): v_active: 1600  v_sync: 1603  v_sync_end
1609 v_blanking: 1646 v_border: 0
[   207.302] (II) RADEON(0): Serial No: CY5520D5UG1
[   207.302] (II) RADEON(0): Monitor name: Cinema HD
[   207.302] (II) RADEON(0): Number of EDID sections to follow: 1
[   207.302] (II) RADEON(0): EDID (in hex):
[   207.303] (II) RADEON(0): 	00ffffffffffff0006103292bf010002
[   207.303] (II) RADEON(0): 	340f01038040287828fe87a3574a9c25
[   207.303] (II) RADEON(0): 	13505400000001010101010101010101
[   207.303] (II) RADEON(0): 	010101010101bc1b00a0502017303020
[   207.303] (II) RADEON(0): 	360081912100001ab06800a0a0402e60
[   207.303] (II) RADEON(0): 	3020360081912100001a000000ff0043
[   207.303] (II) RADEON(0): 	593535323044355547310a00000000fc
[   207.303] (II) RADEON(0): 	0043696e656d612048440a0000000199
[   207.303] (II) RADEON(0): 	40010300000000c04801a500a5000102
[   207.303] (II) RADEON(0): 	031919a8000000000000400000000000
[   207.303] (II) RADEON(0): 	00000000000000000000000000000000
[   207.303] (II) RADEON(0): 	00000000000000000000000000000000
[   207.303] (II) RADEON(0): 	00000000000000000000000000000000
[   207.303] (II) RADEON(0): 	00000000000000000000000000000000
[   207.303] (II) RADEON(0): 	00000000000000000000000000000000
[   207.303] (II) RADEON(0): 	00000000000000000000000000000049
[   207.303] (II) RADEON(0): EDID vendor "APP", prod id 37426
[   207.308] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   207.308] Unhandled monitor type 0

---

### Post by linuxopjemac on 2010-11-29
I see
[ 192.007] Unhandled monitor type 0

Maybe you have to add refresh rates there, so in the Monitor Section add:

```
    HorizSync   30-80
    VertRefresh   50-100

```

---

### Post by linuxopjemac on 2010-11-29
found better values:
```

HorizSync   49-98
VertRefresh 60
```

[http://www.gentoo-wiki.info/Apple_M9179LL-A](http://www.gentoo-wiki.info/Apple_M9179LL-A)

---

### Post by SP3RRFEUER on 2010-11-29
> **linuxopjemac said:**
> I see
[ 192.007] Unhandled monitor type 0

Maybe you have to add refresh rates there, so in the Monitor Section add:

```
    HorizSync   30-80
    VertRefresh   50-100

```

didn't work either

---

### Post by linuxopjemac on 2010-11-29
maybe you have to put this as "Screen" section



```
Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection "Display"
                Depth   24
                Modes   "2560x1600"
    EndSubSection
EndSection

```

---

### Post by SP3RRFEUER on 2010-11-30
> **linuxopjemac said:**
> maybe you have to put this as "Screen" section



```
Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection "Display"
                Depth   24
                Modes   "2560x1600"
    EndSubSection
EndSection

```

screen keeps black

---

### Post by linuxopjemac on 2010-11-30
I ran out of ideas, sorry...

---

### Post by SP3RRFEUER on 2010-11-30
> **linuxopjemac said:**
> I ran out of ideas, sorry...

np, thanks for your help!

---

### Post by khelben1979 on 2010-12-04
I'm curious about one thing: have you ever had a working 2560x1600 screen resolution with that hardware using MacOS X?

Does a lower screen resolution work when changing the screen resolution in the xorg.conf configuration file?

---

### Post by SP3RRFEUER on 2010-12-04
> **khelben1979 said:**
> I'm curious about one thing: have you ever had a working 2560x1600 screen resolution with that hardware using MacOS X?

yep, worked fine with 10.5.8

> **khelben1979 said:**
> Does a lower screen resolution work when changing the screen resolution in the xorg.conf configuration file?

will do testing on monday

---

