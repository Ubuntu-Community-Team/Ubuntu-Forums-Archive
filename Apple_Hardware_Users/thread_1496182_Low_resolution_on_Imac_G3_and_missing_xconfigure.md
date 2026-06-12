---
title: "Low resolution on Imac G3 and missing xconfigure"
date: 2010-05-29
forum: Apple Hardware Users
---

### Post by Maddjokerz on 2010-05-29
I have a snow G3 600 mhz 128mb memory 40 gig hard drive I have just installed ubuntu 10.04 on and it is in low resolution. As I am completely new to ubuntu i have looked up how to change the resolution only to find that my xconfigure is completely blank is there any way to update is or will I have to manually input the xconfigure...I have also tried sudo nano dpkg reconfigure xserver-xorg and it is still blank....

---

### Post by linuxopjemac on 2010-05-29
You need modelines.

Give me the output in a terminal of the following:
```

cvt 1024 768
cvt 800 600
cvt 640 480
```

I will make a working xorg.conf file for you then.

---

### Post by Maddjokerz on 2010-05-29
# 1024x768 59.92 Hz (CVT 0.79M3) hysnc: 47.82 kHz; pclk: 63.50 MHz
Modline "1024x768_60.00"  63.50 1024 1072 1176 1328 768 771 775 798 -hsync +
vsync

# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"  38.25 800 832 912 1024  600 603 607 624 -hsync +vsyn
c

# 640x480 59.38 (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"  23.75  640 664 720 800  480 483 487 500 -hsync +vsync

---

### Post by linuxopjemac on 2010-05-30
Try this one and tell me please if it works. You should also be able to have compiz working.

```
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Driver "ati"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps" "true"
Option "DRI" "true"
EndSection

Section "Module"
  Load "glx"
  Load "dri"
  Load "dbe"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
Modeline "640x480_60.00" 23.75 640 664 720 800 480 483 487 500 -hsync +vsync
Option "PreferredMode" "1024x768_60"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
#InputDevice "Generic Keyboard"
#InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
```

---

### Post by Bunyak on 2010-05-31
Similar problem here... Blue G3 Mac, 600 mHz 40 gig HD.  I currently run Hoary, but would like to upgrade.  BTW, hoary works PERFECTLY, but is no longer supported.  Repositories are a bitch too.

Getting back the issue, it seems to me that your answer to the previous question may work for me too.  However, where do I copy the lines of code to?  Is there a file somewhere that I edit, and what is it called?:confused:

---

### Post by linuxopjemac on 2010-05-31
If you have the same machine, yes:

copy that line of text, then:
```
sudo nano /etc/X11/xorg.conf
```

paste the text into the editor
then CTRL-x and "y" to save.

If you know nothing about gdm/startx I would advize you to simply reboot after that.

---

### Post by Maddjokerz on 2010-05-31
I've been trying to cut and paste into the editor and it's not working is there a command I'm not following?....

---

### Post by linuxopjemac on 2010-05-31
I don't know what you did...

---

### Post by Maddjokerz on 2010-05-31
I used this code and my computer resolution is still on low....:-(

---

### Post by linuxopjemac on 2010-05-31
can you show me the output of:
```

cat /var/log.Xorg.0.log
```

---

### Post by Maddjokerz on 2010-05-31
cat: /var/log.Xorg.0.log: No such file or directory

---

### Post by Bunyak on 2010-05-31
Same issue here.  Made the changes.  saved the file. still low res.

my output is also cat: /var/log.Xorg.0.log: No such file or directory

any more ideas?  sure would be welcome.  BTW, thanks for your help so far :)

---

### Post by Maddjokerz on 2010-06-01
That goes double for me....Thank you so much for helping us....

---

### Post by sha.goyjo on 2010-06-01
> **Maddjokerz said:**
> That goes double for me....Thank you so much for helping us....

It will really make it easier for us to help you guys if you post the current contents of your xorg.conf files. Hell, even attach the file to the post if you need to.

---

### Post by Bunyak on 2010-06-01
OK, will do.  Thanks again, folks.

---

### Post by linuxopjemac on 2010-06-01
it's /var/log/Xorg.0.log

---

### Post by Maddjokerz on 2010-06-01
sorry just copied the code from the line I will try again once I get home from work...

---

### Post by Maddjokerz on 2010-06-01
bash: /var/log/Xorg.0.log: Permission denied

---

### Post by linuxopjemac on 2010-06-02
strange, try
```
sudo cat /var/log/Xorg.0.log
```

this should work (if you are added to the /etc/sudoers file).

---

### Post by Bunyak on 2010-06-02
here's the xorg.conf:

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Driver "ati"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps" "true"
Option "DRI" "true"
EndSection

Section "Module"
  Load "glx"
  Load "dri"
  Load "dbe"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
Modeline "640x480_60.00" 23.75 640 664 720 800 480 483 487 500 -hsync +vsync
Option "PreferredMode" "1024x768_60"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
#InputDevice "Generic Keyboard"
#InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by Bunyak on 2010-06-02
BTW, I think I did a stoopid thing.  Following your earlier posted procedure, I did the save and exit for the updated xorg.conf.  problem is, it saved to root as "xorg.conf.new".  So, I need to move the new config file to /etc/X11 and rename its extension, after saving the original for posterity.  Will give 'er a go, and report back.:)

---

### Post by Bunyak on 2010-06-02
No worky.  :(

---

### Post by Maddjokerz on 2010-06-02
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x58) [0x100b57e8]
1: /usr/bin/X (0x10000000+0x6bce4) [0x1006bce4]
2: (vdso) (__kernel_sigtramp_rt32+0x0) [0x100370]
3: /usr/lib/xorg/modules/libint10.so (xf86ExtendedInitInt10+0x380) [0xf772e40]
4: /usr/lib/xorg/modules/libint10.so (xf86InitInt10+0x28) [0xf76eba8]
5: /usr/lib/xorg/modules/drivers/r128_drv.so (0xf7b5000+0x10dbc) [0xf7c5dbc]
6: /usr/bin/X (InitOutput+0x5cc) [0x1007d59c]
7: /usr/bin/X (0x10000000+0x1d218) [0x1001d218]
8: /lib/libc.so.6 (0xfaff000+0x1f73c) [0xfb1e73c]
9: /lib/libc.so.6 (0xfaff000+0x1f900) [0xfb1e900]
Bus error at address 0x48168000

Caught signal 7 (Bus error). Server aborting

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by linuxopjemac on 2010-06-03
```
sudo cat /var/log/Xorg.0.log
```

I don't know why you don't give us that info...I asked you a few times.

---

### Post by Maddjokerz on 2010-06-03
```
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x58) [0x100b57e8]
1: /usr/bin/X (0x10000000+0x6bce4) [0x1006bce4]
2: (vdso) (__kernel_sigtramp_rt32+0x0) [0x100370]
3: /usr/lib/xorg/modules/libint10.so (xf86ExtendedInitInt10+0x380) [0xf772e40]
4: /usr/lib/xorg/modules/libint10.so (xf86InitInt10+0x28) [0xf76eba8]
5: /usr/lib/xorg/modules/drivers/r128_drv.so (0xf7b5000+0x10dbc) [0xf7c5dbc]
6: /usr/bin/X (InitOutput+0x5cc) [0x1007d59c]
7: /usr/bin/X (0x10000000+0x1d218) [0x1001d218]
8: /lib/libc.so.6 (0xfaff000+0x1f73c) [0xfb1e73c]
9: /lib/libc.so.6 (0xfaff000+0x1f900) [0xfb1e900]
Bus error at address 0x48168000

Caught signal 7 (Bus error). Server aborting

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

Sorry I thought I put the right code in....

---

### Post by linuxopjemac on 2010-06-04
Sorry, I can't help if you don't do what I ask you to do........

> Please also check the log file at "/var/log/Xorg.0.log" for additional information.


---

### Post by Bunyak on 2010-06-04
Here's mine.  I think this is what you need to help me troubleshoot this issue:

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux user-desktop 2.6.32-21-powerpc #32-Ubuntu Fri Apr 16 08:10:47 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash video=ofonly 
Build Date: 23 April 2010  05:11:55PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  4 07:10:23 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x101ebbe4
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:16:0) 1002:5452:1002:5452 ATI Technologies Inc Rage 128 Pro Ultra TR rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.8.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) R128(0): PCI bus 0 card 16 func 0
(==) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "r128"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by linuxopjemac on 2010-06-04
Bunyak: are you sure you have this line in the Device section ?

```
Option "UseFBDev" "false"
```

---

### Post by Maddjokerz on 2010-06-04
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.31-20-powerpc64-smp ppc Ubuntu
Current Operating System: Linux maddjokerz-desktop 2.6.32-22-powerpc #35-Ubuntu Tue Jun 1 14:17:52 UTC 2010 ppc
Kernel command line: root=/dev/hda3 ro quiet splash video=ofonly 
Build Date: 23 April 2010  05:11:55PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  4 21:25:11 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
(**) Option "AIGLX" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x101ebbe4
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:16:0) 1002:5452:1002:5452 ATI Technologies Inc Rage 128 Pro Ultra TR rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
(II) Open APM successful
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.8.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(II) R128(0): PCI bus 0 card 16 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(**) R128(0): Option "SWcursor" "true"
(**) R128(0): Option "ForcePCIMode" "true"
(**) R128(0): Option "UseFBDev" "false"
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): initializing int10

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x58) [0x100b57e8]
1: /usr/bin/X (0x10000000+0x6bce4) [0x1006bce4]
2: (vdso) (__kernel_sigtramp_rt32+0x0) [0x100370]
3: /usr/lib/xorg/modules/libint10.so (xf86ExtendedInitInt10+0x380) [0xf772e40]
4: /usr/lib/xorg/modules/libint10.so (xf86InitInt10+0x28) [0xf76eba8]
5: /usr/lib/xorg/modules/drivers/r128_drv.so (0xf7b5000+0x10dbc) [0xf7c5dbc]
6: /usr/bin/X (InitOutput+0x5cc) [0x1007d59c]
7: /usr/bin/X (0x10000000+0x1d218) [0x1001d218]
8: /lib/libc.so.6 (0xfaff000+0x1f73c) [0xfb1e73c]
9: /lib/libc.so.6 (0xfaff000+0x1f900) [0xfb1e900]
Bus error at address 0x48168000

Caught signal 7 (Bus error). Server aborting


``` sorry didn't copy the whole thing down correctly that's my fault....

---

### Post by Bunyak on 2010-06-05
> **linuxopjemac said:**
> Bunyak: are you sure you have this line in the Device section ?

```
Option "UseFBDev" "false"
```

Well... I think Ubuntu security update changed the xorg.conf file.  I have changed xorg.conf to your suggested version, and will give it a try now.  As for "UseFBDev" "false" yes it is in there under device.  Exactly as you had written it.  Will let you know how it works.

---

### Post by linuxopjemac on 2010-06-05
Maddjokerz: I see the problem for you. Put this in the Device Section

```
Option "NoInt10" "true"
```

If everything works, post the working Xorg.conf for other to read and try please.

Good luck

---

### Post by Maddjokerz on 2010-06-05
Thank you  linxopjemac for all your help that worked completely and sorry for the earlier codes that were not what you were looking for...the new xconfigure is

```
Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Driver "ati"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps" "true"
Option "DRI" "true"
Option "NoInt10" "true"
EndSection

Section "Module"
  Load "glx"
  Load "dri"
  Load "dbe"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsy$
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
Modeline "640x480_60.00" 23.75 640 664 720 800 480 483 487 500 -hsync +vsync
Option "PreferredMode" "1024x768_60"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
#InputDevice "Generic Keyboard"
#InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
Option "AIGLX" "true"
EndSection

Identifier "Default Layout"
Screen "Default Screen"
#InputDevice "Generic Keyboard"
#InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
  

```

---

### Post by Bunyak on 2010-06-05
> **linuxopjemac said:**
> Maddjokerz: I see the problem for you. Put this in the Device Section

```
Option "NoInt10" "true"
```

If everything works, post the working Xorg.conf for other to read and try please.

Good luck


Works Great!  Thank you ever so much.  My entire computer is also SO MUCH FASTER!  Here's my xorg.conf:

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Driver "ati"
Option "UseFBDev" "false"
Option "SWcursor" "true"
Option "ForcePCIMode" "true"
Option "XAANoOffscreenPixmaps" "true"
Option "DRI" "true"
Option "NoInt10" "true"
EndSection

Section "Module"
  Load "glx"
  Load "dri"
  Load "dbe"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 58-62
VertRefresh 75-117
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
Modeline "640x480_60.00" 23.75 640 664 720 800 480 483 487 500 -hsync +vsync
Option "PreferredMode" "1024x768_60"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 Pro Ultra TR"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
#InputDevice "Generic Keyboard"
#InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by linuxopjemac on 2010-06-05
GREAT! I will post this working xorg.conf file on my own site for future reference.

[http://mac.linux.be/content/cross-distribution-issues](http://mac.linux.be/content/cross-distribution-issues)

---

### Post by Maddjokerz on 2010-06-07
Thank you for fixing our problems but how did you do that for future refrenece

---

### Post by linuxopjemac on 2010-06-07
Maddjokerz: I don't understand your question.

I put the info on my own site, for other people to find easily. It can be found [here]("http://mac.linux.be/content/g3-imac-tray-loader-slotloader-all-versions-xorgconf"). Scroll down and you will find the xorg.conf file you are using.

---

### Post by Maddjokerz on 2010-06-08
My question is how you were able to decipher  the cat /var/log.Xorg.0.log code ?

---

### Post by linuxopjemac on 2010-06-08
> (II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Video Driver, version 6.0
(II) R128(0): initializing int10

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x58) [0x100b57e8]
1: /usr/bin/X (0x10000000+0x6bce4) [0x1006bce4]
2: (vdso) (__kernel_sigtramp_rt32+0x0) [0x100370]
3: /usr/lib/xorg/modules/libint10.so (xf86ExtendedInitInt10+0x380) [0xf772e40]
4: /usr/lib/xorg/modules/libint10.so (xf86InitInt10+0x28) [0xf76eba8]
5: /usr/lib/xorg/modules/drivers/r128_drv.so (0xf7b5000+0x10dbc) [0xf7c5dbc]
6: /usr/bin/X (InitOutput+0x5cc) [0x1007d59c]
7: /usr/bin/X (0x10000000+0x1d218) [0x1001d218]
8: /lib/libc.so.6 (0xfaff000+0x1f73c) [0xfb1e73c]
9: /lib/libc.so.6 (0xfaff000+0x1f900) [0xfb1e900]
Bus error at address 0x48168000

Caught signal 7 (Bus error). Server aborting

You can see that it borks at int10. I know this problem. You can prevent it with the Option I gave.

---

