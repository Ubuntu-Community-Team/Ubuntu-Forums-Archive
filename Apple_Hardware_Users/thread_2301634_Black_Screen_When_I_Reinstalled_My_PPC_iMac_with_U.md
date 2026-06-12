---
title: "Black Screen When I Reinstalled My PPC iMac with Ubuntu 14.04."
date: 2015-11-03
forum: Apple Hardware Users
---

### Post by Jacob_Ritorto on 2015-11-03
Greetings all,
  My nice MBA got rained on the other day, so I'm stuck with what appears to be a second edition, "five-flavours," PowerPC "Firewire" iMac, [http://lowendmac.com/1999/400-mhz-imac-dv-late-1999](http://lowendmac.com/1999/400-mhz-imac-dv-late-1999) .   I've run ubuntu 13.10 on it just fine before, X11 working and all.  But support on that release ended some time ago, so I reinstalled the machine with 14.04.

  X11 is now broken.  The screen on virtual console 7 is just black.  I can switch to other virtual consoles and see text and the system is otherwise running fine.  I've tried a number of the remedies listed on various forums with no real results, so after all that tweaking I reinstalled 14.04 once again to start from a freshly-installed system.  I did run apt-get update and upgrade to bring things up to current.  Please see Xorg.0.log below.  

  Would anyone happen to be familiar with this failure mode, or do I need to become an expert?

thx
jake

```
root@bluthing:~# !!
cat /var/log/Xorg.0.log
[    58.915]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    58.915] X Protocol Version 11, Revision 0
[    58.934] Build Operating System: Linux 3.13.0-45-powerpc64-smp ppc Ubuntu
[    58.934] Current Operating System: Linux bluthing 3.13.0-24-powerpc-smp #47-Ubuntu SMP Sat May 3 02:03:13 UTC 2014 ppc
[    58.934] Kernel command line: root=UUID=f3500dc8-f781-499f-856c-5e81193afaf5 ro quiet splash
[    58.935] Build Date: 12 February 2015  02:53:48PM
[    58.935] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    58.935] Current version of pixman: 0.30.2
[    58.935] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    58.935] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    58.966] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov  3 21:19:52 2015
[    59.000] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    59.021] (==) No Layout section.  Using the first Screen section.
[    59.022] (==) No screen section available. Using defaults.
[    59.022] (**) |-->Screen "Default Screen Section" (0)
[    59.022] (**) |   |-->Monitor "<default monitor>"
[    59.034] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    59.045] (**) |   |-->Device "Card0"
[    59.045] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    59.045] (==) Automatically adding devices
[    59.045] (==) Automatically enabling devices
[    59.045] (==) Automatically adding GPU devices
[    59.056] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    59.057] 	Entry deleted from font path.
[    59.057] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    59.057] 	Entry deleted from font path.
[    59.057] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    59.068] 	Entry deleted from font path.
[    59.068] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    59.068] 	Entry deleted from font path.
[    59.068] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    59.069] 	Entry deleted from font path.
[    59.069] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    59.069] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    59.069] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    59.069] (II) Loader magic: 0x20837694
[    59.069] (II) Module ABI versions:
[    59.076] 	X.Org ANSI C Emulation: 0.4
[    59.076] 	X.Org Video Driver: 15.0
[    59.077] 	X.Org XInput driver : 20.0
[    59.077] 	X.Org Server Extension : 8.0
[    59.122] (--) PCI:*(0:0:16:0) 1002:5052:1002:5052 rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    59.137] Initializing built-in extension Generic Event Extension
[    59.137] Initializing built-in extension SHAPE
[    59.137] Initializing built-in extension MIT-SHM
[    59.137] Initializing built-in extension XInputExtension
[    59.138] Initializing built-in extension XTEST
[    59.138] Initializing built-in extension BIG-REQUESTS
[    59.138] Initializing built-in extension SYNC
[    59.138] Initializing built-in extension XKEYBOARD
[    59.138] Initializing built-in extension XC-MISC
[    59.138] Initializing built-in extension SECURITY
[    59.151] Initializing built-in extension XINERAMA
[    59.153] Initializing built-in extension XFIXES
[    59.153] Initializing built-in extension RENDER
[    59.153] Initializing built-in extension RANDR
[    59.153] Initializing built-in extension COMPOSITE
[    59.153] Initializing built-in extension DAMAGE
[    59.154] Initializing built-in extension MIT-SCREEN-SAVER
[    59.154] Initializing built-in extension DOUBLE-BUFFER
[    59.154] Initializing built-in extension RECORD
[    59.154] Initializing built-in extension DPMS
[    59.154] Initializing built-in extension Present
[    59.165] Initializing built-in extension DRI3
[    59.165] Initializing built-in extension X-Resource
[    59.165] Initializing built-in extension XVideo
[    59.165] Initializing built-in extension XVideo-MotionCompensation
[    59.165] Initializing built-in extension SELinux
[    59.165] Initializing built-in extension XFree86-VidModeExtension
[    59.165] Initializing built-in extension XFree86-DGA
[    59.166] Initializing built-in extension XFree86-DRI
[    59.166] Initializing built-in extension DRI2
[    59.166] (WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
[    59.166] (II) "glx" will be loaded by default.
[    59.166] (WW) "xmir" is not to be loaded by default. Skipping.
[    59.166] (II) LoadModule: "glx"
[    59.213] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    59.501] (II) Module glx: vendor="X.Org Foundation"
[    59.501] 	compiled for 1.15.1, module version = 1.0.0
[    59.502] 	ABI class: X.Org Server Extension, version 8.0
[    59.502] (==) AIGLX enabled
[    59.502] Loading extension GLX
[    59.502] (II) LoadModule: "r128"
[    59.530] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    59.531] (II) Module r128: vendor="X.Org Foundation"
[    59.531] 	compiled for 1.15.0, module version = 6.9.2
[    59.531] 	Module class: X.Org Video Driver
[    59.531] 	ABI class: X.Org Video Driver, version 15.0
[    59.554] (II) R128: Driver for ATI Rage 128 chipsets:
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
[    59.582] (++) using VT number 7


[    59.585] (II) R128(0): PCI bus 0 card 16 func 0
[    59.585] (II) R128(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    59.585] (==) R128(0): Depth 24, (--) framebuffer bpp 32
[    59.585] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    59.586] (==) R128(0): Default visual is TrueColor
[    59.586] (**) R128(0): Option "UseFBDev" "False"
[    59.586] (II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
[    59.586] (==) R128(0): RGB weight 888
[    59.586] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    59.587] (II) Loading sub module "int10"
[    59.587] (II) LoadModule: "int10"
[    59.599] (II) Loading /usr/lib/xorg/modules/libint10.so
[    59.612] (II) Module int10: vendor="X.Org Foundation"
[    59.612] 	compiled for 1.15.1, module version = 1.0.0
[    59.612] 	ABI class: X.Org Video Driver, version 15.0
[    59.613] (II) R128(0): initializing int10
[    59.622] (**) R128(0): Option "NoINT10" "True"
[    59.623] (--) R128(0): Chipset: "ATI Rage 128 Pro VR PR (PCI)" (ChipID = 0x5052)
[    59.623] (--) R128(0): Linear framebuffer at 0x94000000
[    59.623] (--) R128(0): MMIO registers at 0x90000000
[    59.628] (--) R128(0): VideoRAM: 8192 kByte (64-bit SDR SGRAM 2:1)
[    59.628] (**) R128(0): Using external CRT for display
[    59.629] (WW) R128(0): Failed to read PCI ROM!
[    59.638] (WW) R128(0): Video BIOS not found!
[    59.638] (II) R128(0): Primary Display == Type 3
[    59.638] (WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
[    59.639] (II) R128(0): PLL parameters: rf=2950 rd=26 min=12500 max=25000; xclk=7150
[    59.639] (II) Loading sub module "ddc"
[    59.639] (II) LoadModule: "ddc"
[    59.650] (II) Module "ddc" already built-in
[    59.651] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    59.659] (II) Loading sub module "i2c"
[    59.659] (II) LoadModule: "i2c"
[    59.659] (II) Module "i2c" already built-in
[    59.665] (II) R128(0): I2C bus "DDC" initialized.
[    59.666] (II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
[    59.682] (EE) R128(0): No DFP detected
[    59.693] (II) R128(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    59.693] (II) R128(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    59.693] (II) R128(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    59.694] (WW) R128(0): Unable to estimate virtual size
[    59.694] (II) R128(0): Clock range:  12.50 to 250.00 MHz
[    59.694] (II) R128(0): Not using default mode "640x350" (vrefresh out of range)
[    59.694] (II) R128(0): Not using default mode "320x175" (vrefresh out of range)
[    59.694] (II) R128(0): Not using default mode "640x400" (vrefresh out of range)
[    59.703] (II) R128(0): Not using default mode "320x200" (vrefresh out of range)
[    59.703] (II) R128(0): Not using default mode "720x400" (vrefresh out of range)
[    59.703] (II) R128(0): Not using default mode "360x200" (vrefresh out of range)
[    59.711] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    59.711] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    59.711] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    59.711] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    59.711] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    59.719] (II) R128(0): Not using default mode "320x240" (vrefresh out of range)
[    59.719] (II) R128(0): Not using default mode "800x600" (vrefresh out of range)
[    59.719] (II) R128(0): Not using default mode "400x300" (vrefresh out of range)
[    59.719] (II) R128(0): Not using default mode "800x600" (vrefresh out of range)
[    59.719] (II) R128(0): Not using default mode "400x300" (vrefresh out of range)
[    59.728] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    59.728] (II) R128(0): Not using default mode "400x300" (hsync out of range)
[    59.730] (II) R128(0): Not using default mode "1024x768i" (vrefresh out of range)
[    59.731] (II) R128(0): Not using default mode "512x384i" (vrefresh out of range)
[    59.731] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    59.731] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[    59.731] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    59.731] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[    59.731] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    59.737] (II) R128(0): Not using default mode "512x384" (hsync out of range)
[    59.737] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    59.737] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    59.737] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    59.738] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    59.738] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    59.738] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    59.738] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    59.738] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    59.748] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    59.748] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    59.748] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    59.749] (II) R128(0): Not using default mode "640x512" (hsync out of range)
[    59.749] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    59.749] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    59.749] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    59.749] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    59.749] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    59.749] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    59.750] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    59.750] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    59.750] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    59.750] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    59.750] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    59.750] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[    59.750] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    59.750] (II) R128(0): Not using default mode "896x672" (hsync out of range)
[    59.751] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    59.751] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[    59.751] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    59.751] (II) R128(0): Not using default mode "928x696" (hsync out of range)
[    59.751] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    59.751] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    59.751] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    59.771] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    59.774] (II) R128(0): Not using default mode "832x624" (hsync out of range)
[    59.774] (II) R128(0): Not using default mode "416x312" (hsync out of range)
[    59.774] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    59.774] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    59.774] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    59.774] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    59.775] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    59.775] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    59.775] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    59.775] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    59.775] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    59.775] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    59.775] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    59.789] (II) R128(0): Not using default mode "576x432" (hsync out of range)
[    59.789] (II) R128(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    59.790] (II) R128(0): Not using default mode "1360x768" (mode clock too high)
[    59.790] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    59.790] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    59.790] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    59.790] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    59.790] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    59.791] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    59.791] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    59.791] (II) R128(0): Not using default mode "700x525" (hsync out of range)
[    59.791] (II) R128(0): Not using default mode "1440x900" (hsync out of range)
[    59.791] (II) R128(0): Not using default mode "720x450" (hsync out of range)
[    59.791] (II) R128(0): Not using default mode "1600x1024" (hsync out of range)
[    59.791] (II) R128(0): Not using default mode "800x512" (hsync out of range)
[    59.805] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    59.805] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    59.805] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    59.806] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    59.806] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    59.806] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    59.806] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    59.806] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    59.806] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    59.806] (II) R128(0): Not using default mode "840x525" (hsync out of range)
[    59.807] (II) R128(0): Not using default mode "1920x1080" (hsync out of range)
[    59.807] (II) R128(0): Not using default mode "960x540" (hsync out of range)
[    59.807] (II) R128(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    59.807] (II) R128(0): Not using default mode "960x600" (hsync out of range)
[    59.807] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    59.816] (II) R128(0): Not using default mode "960x720" (hsync out of range)
[    59.816] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    59.816] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    59.817] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    59.817] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    59.817] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    59.817] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    59.817] (--) R128(0): Virtual size is 1024x768 (pitch 1024)
[    59.817] (**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    59.818] (II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz zd)
[    59.818] (**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    59.818] (II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz zd)
[    59.818] (**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    59.818] (II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz zd)
[    59.818] (**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    59.819] (II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz zd)
[    59.819] (**) R128(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    59.819] (II) R128(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz zd)
[    59.819] (**) R128(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    59.819] (II) R128(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz zd)
[    59.819] (**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    59.837] (II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz zd)
[    59.837] (**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    59.837] (II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz zd)
[    59.837] (**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    59.838] (II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz zd)
[    59.838] (**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    59.838] (II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz zd)
[    59.838] (==) R128(0): DPI set to (96, 96)
[    59.838] (II) Loading sub module "fb"
[    59.838] (II) LoadModule: "fb"
[    59.865] (II) Loading /usr/lib/xorg/modules/libfb.so
[    59.879] (II) Module fb: vendor="X.Org Foundation"
[    59.879] 	compiled for 1.15.1, module version = 1.0.0
[    59.879] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    59.879] (II) Loading sub module "ramdac"
[    59.890] (II) LoadModule: "ramdac"
[    59.892] (II) Module "ramdac" already built-in
[    59.895] (II) Loading sub module "shadowfb"
[    59.896] (II) LoadModule: "shadowfb"
[    59.911] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    59.925] (II) Module shadowfb: vendor="X.Org Foundation"
[    59.925] 	compiled for 1.15.1, module version = 1.0.0
[    59.926] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    59.926] (II) R128(0): Page flipping disabled
[    59.926] (!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
[    59.926] (--) Depth 24 pixmap format is 32 bpp
[    59.939] (II) R128(0): Acceleration of RENDER operations will be enabled upon successful loading of DRI and EXA
[    59.954] (WW) R128(0): Static buffer allocation failed -- need at least 9216 kB video memory
[    59.955] (II) R128(0): Filling in EXA memory info
[    59.955] (II) R128(0): Loading EXA module...
[    59.955] (II) Loading sub module "exa"
[    59.955] (II) LoadModule: "exa"
[    59.968] (II) Loading /usr/lib/xorg/modules/libexa.so
[    59.970] (II) Module exa: vendor="X.Org Foundation"
[    59.970] 	compiled for 1.15.1, module version = 2.6.0
[    59.982] 	ABI class: X.Org Video Driver, version 15.0
[    59.982] (II) R128(0): Allocating EXA driver...
[    59.983] (II) R128(0): Acceleration enabled
[    59.983] (II) R128(0): Filled in offs
[    59.983] (II) R128(0): Going to init EXA...
[    59.983] (II) R128(0): Setting up EXA callbacks
[    59.983] (II) R128(0): Initalizing 2D acceleration engine...
[    59.990] (II) R128(0): Initializing EXA driver...
[    59.991] (II) EXA(0): Offscreen pixmap area of 5242880 bytes
[    59.991] (II) EXA(0): Driver registered support for the following operations:
[    59.991] (II)         Solid
[    59.996] (II)         Copy
[    59.996] (II) R128(0): EXA Acceleration enabled
[    59.998] (==) R128(0): Backing store enabled
[    59.998] (==) R128(0): Silken mouse enabled
[    60.001] (II) R128(0): Using hardware cursor (scanline 8190)
[    60.024] (==) R128(0): DPMS enabled
[    60.025] (WW) R128(0): Direct rendering disabled
[    60.025] (==) RandR enabled
[    60.558] (II) SELinux: Disabled on system
[    60.631] (II) AIGLX: Screen 0 is not DRI2 capable
[    60.643] (EE) AIGLX: reverting to software rendering
[    61.090] (II) AIGLX: Loaded and initialized swrast
[    61.094] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    62.123] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    62.392] (II) config/udev: Adding input device PowerMac Beep (/dev/input/event1)
[    62.394] (II) No input driver specified, ignoring this device.
[    62.394] (II) This device may have been added with another device file.
[    62.425] (II) config/udev: Adding input device Mitsumi Electric Apple USB Keyboard (/dev/input/event2)
[    62.433] (**) Mitsumi Electric Apple USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    62.434] (II) LoadModule: "evdev"
[    62.447] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    62.487] (II) Module evdev: vendor="X.Org Foundation"
[    62.487] 	compiled for 1.15.0, module version = 2.8.2
[    62.488] 	Module class: X.Org XInput Driver
[    62.488] 	ABI class: X.Org XInput driver, version 20.0
[    62.488] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple USB Keyboard'
[    62.489] (**) Mitsumi Electric Apple USB Keyboard: always reports core events
[    62.489] (**) evdev: Mitsumi Electric Apple USB Keyboard: Device: "/dev/input/event2"
[    62.489] (--) evdev: Mitsumi Electric Apple USB Keyboard: Vendor 0x5ac Product 0x201
[    62.490] (--) evdev: Mitsumi Electric Apple USB Keyboard: Found keys
[    62.490] (II) evdev: Mitsumi Electric Apple USB Keyboard: Configuring as keyboard
[    62.490] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2/event2"
[    62.501] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple USB Keyboard" (type: KEYBOARD, id 6)
[    62.501] (**) Option "xkb_rules" "evdev"
[    62.501] (**) Option "xkb_model" "pc105"
[    62.502] (**) Option "xkb_layout" "us"
[    62.549] (II) config/udev: Adding input device Logitech M4848 (/dev/input/event3)
[    62.553] (**) Logitech M4848: Applying InputClass "evdev pointer catchall"
[    62.554] (II) Using input driver 'evdev' for 'Logitech M4848'
[    62.554] (**) Logitech M4848: always reports core events
[    62.559] (**) evdev: Logitech M4848: Device: "/dev/input/event3"
[    62.559] (--) evdev: Logitech M4848: Vendor 0x5ac Product 0x301
[    62.564] (--) evdev: Logitech M4848: Found 1 mouse buttons
[    62.564] (--) evdev: Logitech M4848: Found relative axes
[    62.564] (--) evdev: Logitech M4848: Found x and y relative axes
[    62.565] (II) evdev: Logitech M4848: Configuring as mouse
[    62.565] (**) evdev: Logitech M4848: YAxisMapping: buttons 4 and 5
[    62.565] (**) evdev: Logitech M4848: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    62.565] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input3/event3"
[    62.566] (II) XINPUT: Adding extended input device "Logitech M4848" (type: MOUSE, id 7)
[    62.574] (II) evdev: Logitech M4848: initialized for relative axes.
[    62.589] (**) Logitech M4848: (accel) keeping acceleration scheme 1
[    62.593] (**) Logitech M4848: (accel) acceleration profile 0
[    62.593] (**) Logitech M4848: (accel) acceleration factor: 2.000
[    62.593] (**) Logitech M4848: (accel) acceleration threshold: 4
[    62.606] (II) config/udev: Adding input device Logitech M4848 (/dev/input/mouse0)
[    62.631] (II) No input driver specified, ignoring this device.
[    62.631] (II) This device may have been added with another device file.
[    62.795] (II) config/udev: Adding input device PMU (/dev/input/event0)
[    62.805] (**) PMU: Applying InputClass "evdev keyboard catchall"
[    62.805] (II) Using input driver 'evdev' for 'PMU'
[    62.805] (**) PMU: always reports core events
[    62.813] (**) evdev: PMU: Device: "/dev/input/event0"
[    62.815] (--) evdev: PMU: Vendor 0x1 Product 0x1
[    62.815] (--) evdev: PMU: Found keys
[    62.815] (II) evdev: PMU: Configuring as keyboard
[    62.823] (**) Option "config_info" "udev:/sys/devices/virtual/input/input0/event0"
[    62.830] (II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD, id 8)
[    62.831] (**) Option "xkb_rules" "evdev"
[    62.831] (**) Option "xkb_model" "pc105"
[    62.831] (**) Option "xkb_layout" "us"
[    62.878] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
[    62.886] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    62.890] (II) Using input driver 'evdev' for 'Macintosh mouse button emulation'
[    62.890] (**) Macintosh mouse button emulation: always reports core events
[    62.895] (**) evdev: Macintosh mouse button emulation: Device: "/dev/input/event4"
[    62.895] (--) evdev: Macintosh mouse button emulation: Vendor 0x1 Product 0x1
[    62.901] (--) evdev: Macintosh mouse button emulation: Found 3 mouse buttons
[    62.901] (--) evdev: Macintosh mouse button emulation: Found relative axes
[    62.901] (--) evdev: Macintosh mouse button emulation: Found x and y relative axes
[    62.902] (II) evdev: Macintosh mouse button emulation: Configuring as mouse
[    62.902] (**) evdev: Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    62.902] (**) evdev: Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    62.908] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    62.909] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE, id 9)
[    62.909] (II) evdev: Macintosh mouse button emulation: initialized for relative axes.
[    62.922] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    62.928] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    62.928] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    62.928] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    62.931] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse1)
[    62.931] (II) No input driver specified, ignoring this device.
[    62.947] (II) This device may have been added with another device file.
[    63.404] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse2)
[    63.408] (II) No input driver specified, ignoring this device.
[    63.409] (II) This device may have been added with another device file.
[    65.306] (II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event5)
[    65.307] (**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
[    65.307] (II) Using input driver 'evdev' for 'Mouseemu virtual keyboard'
[    65.307] (**) Mouseemu virtual keyboard: always reports core events
[    65.309] (**) evdev: Mouseemu virtual keyboard: Device: "/dev/input/event5"
[    65.310] (--) evdev: Mouseemu virtual keyboard: Vendor 0x1f Product 0x1f
[    65.310] (--) evdev: Mouseemu virtual keyboard: Found keys
[    65.310] (II) evdev: Mouseemu virtual keyboard: Configuring as keyboard
[    65.310] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    65.311] (II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD, id 10)
[    65.311] (**) Option "xkb_rules" "evdev"
[    65.311] (**) Option "xkb_model" "pc105"
[    65.332] (**) Option "xkb_layout" "us"
[    65.365] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event6)
[    65.366] (**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
[    65.366] (II) Using input driver 'evdev' for 'Mouseemu virtual mouse'
[    65.366] (**) Mouseemu virtual mouse: always reports core events
[    65.366] (**) evdev: Mouseemu virtual mouse: Device: "/dev/input/event6"
[    65.367] (--) evdev: Mouseemu virtual mouse: Vendor 0x1f Product 0x1e
[    65.367] (--) evdev: Mouseemu virtual mouse: Found 15 mouse buttons
[    65.367] (--) evdev: Mouseemu virtual mouse: Found scroll wheel(s)
[    65.367] (--) evdev: Mouseemu virtual mouse: Found relative axes
[    65.367] (--) evdev: Mouseemu virtual mouse: Found x and y relative axes
[    65.367] (II) evdev: Mouseemu virtual mouse: Configuring as mouse
[    65.377] (II) evdev: Mouseemu virtual mouse: Adding scrollwheel support
[    65.377] (**) evdev: Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
[    65.377] (**) evdev: Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.377] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    65.378] (II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE, id 11)
[    65.378] (II) evdev: Mouseemu virtual mouse: initialized for relative axes.
[    65.396] (**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
[    65.396] (**) Mouseemu virtual mouse: (accel) acceleration profile 0
[    65.397] (**) Mouseemu virtual mouse: (accel) acceleration factor: 2.000
[    65.397] (**) Mouseemu virtual mouse: (accel) acceleration threshold: 4
```

---

### Post by Roger-H on 2015-11-04
Do you have the Lubuntu 14.04.2 CD handy, and are you able to boot it using the video=ofonly flag described in the boot message?

---

### Post by abtabt on 2015-11-04
read [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics)

ATI Rage 128 cards 

you need a xorg.conf

or if you have second port VGA then you can use that, not need any xorg.conf

---

### Post by Jacob_Ritorto on 2015-11-04
yes, I did try the yaboot parameters recommended.  nomodeset, offb=off, video=ofonly, each separately.  No affect on the X11 virtual console (though I did see different text-mode character renderings, so it seems that the parameters did affect _something_).

So, abtabt, you think it's just not getting a legit scan rate to satisfy the analog stuff in the crt, then?   I'll try hooking up an external multisync-style screen to the vga port.. 

  I've used regular X more than Xorg, so I have a bit of a learning curve, here, especially now that there's this xorg.d heirarchy thing.  Will Xorg find my conf file, like in the days of yore, if I simply place my custom xorg.conf in /etc/?  

  Did you think that the autosized scan rates that Xorg decided upon in my logfile were bad?

OK, quick update: I hooked up a 17" Apple Studio Display (appears to be a nice multisync Trinitron CRT) to the iMac's built-in VGA port and I'm getting perfect X display with the standard 14.04.2 ppc desktop install distro.  So my whole poor experience in this thread comes down to just a problem with the iMac's built-in display stuff (or misconfigured Xorg, if you want to look at it from the software perspective).  Does anyone know the proper sync stuff to make this tube happy? If not, I'll experiment and report back my findings.  

 This exercise should probably result in some Xorg config conditionals in the new 16.04 release so others don't experience these confusing black screens in the future.  I'm happy to help with the code if somebody can hold my hand through the ubuntu upstream process a little -- while I'm quite familiar with lots of unix dev, git, c, etc., this would be my first serious foray into ubuntu development.

---

### Post by rsavage on 2015-11-04
I'm not sure you'll ever fully get rid of an xorg.conf file - see [https://bugs.freedesktop.org/show_bug.cgi?id=91358](https://bugs.freedesktop.org/show_bug.cgi?id=91358)

The iMac G3 has always been problematic, which is why it gets a special mention in the PowerPC documentation, which er...., you don't seem to have read properly?

Your xorg.0.log says you are using an xorg.conf, and I see from the log you're using unrecommended values.

I don't think anybody has reported the problem properly though.  If you want to have a go at fixing the code then I would create a new bug on freedesktop and attach your patch.  I've always found Connor Beham (the r128 maintainer) to be a really helpful guy.  If it gets accepted then it will find its way into Ubuntu through debian once its been packaged and tested.  Sometimes you need to prod things on launchpad if things aren't happening fast enough.

If you don't think the PowerPC documentation is clear enough (which you obviously don't since you've missed it), then please feel free to edit it to your hearts content.  Very few iMac G3 users seem to be using 14.04, so there could easily be room for improvement.

---

### Post by Jacob_Ritorto on 2015-11-05
Thanks again for the replies, rsavage and others.  
> **rsavage said:**
> 
The iMac G3 has always been problematic, which is why it gets a special mention in the PowerPC documentation, which er...., you don't seem to have read properly?


Closest I came to finding what I thought was authoritative ppc documentation (after googling and searching ubuntu sites) was this: [https://wiki.ubuntu.com/PowerPCFAQ#ATI_Rage_128_cards](https://wiki.ubuntu.com/PowerPCFAQ#ATI_Rage_128_cards) and I followed it verbatim but got no results.  I suspect my confusion there stems from the fact that there's an xorg.conf.d hierarchy instead of a monolithic one-file approach.  I made up my own local file with the contents recommended in link above and tucked it into the xorg.xonf.d directory but it seemed to not change things at all, so I moved on to other recommendations.  So yeah, some illumination might be good here and I'm happy to help if I can.  Am I at least pointing in the right direction?  Maybe not because I've still not found any specific xorg.conf sync rate recommendations like you mentioned.  Hate to cheat, but is there another link I should be looking at?


> **rsavage said:**
> 
 Your xorg.0.log says you are using an xorg.conf, and I see from the log you're using unrecommended values.

 
I looked at that log again and didn't see evidence of an xorg.conf file, just the xorf.conf.d hierarchy.  This is a run after a fresh os install because I'd tweaked so much of the previous instance of the system that I figured I'd ruined it and wanted a clean slate. So those are default values and I still need to find recommended values and to find out how to plug them in properly.


> **rsavage said:**
> 
I don't think anybody has reported the problem properly though.  If you want to have a go at fixing the code then I would create a new bug on freedesktop and attach your patch.  I've always found Connor Beham (the r128 maintainer) to be a really helpful guy.  If it gets accepted then it will find its way into Ubuntu through debian once its been packaged and tested.  Sometimes you need to prod things on launchpad if things aren't happening fast enough.


Good leads,thanks.. I'll start chasing that down..

> **rsavage said:**
> 
 If you don't think the PowerPC documentation is clear enough (which you obviously don't since you've missed it), then please feel free to edit it to your hearts content.  Very few iMac G3 users seem to be using 14.04, so there could easily be room for improvement.

yup.

---

### Post by rsavage on 2015-11-05
Early imac g3s didin't have rage128 cards, so when I wrote the documentation I didn't think it was appropriate to put everything in the rage 128 section.  So info on configuring a monitor is in, unsurprisingly, the section that covers configuring a monitor -  [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F)

The problem is people don't want to read the documentation or they come with their own fixed ideas and won't be told.  They just pick out bits that look easiest, even when the documentation says it doesn't apply to them.  They then get frustrated, have a paddy and come on here.  Spending 5 mins reading the documentation as it was intended would save them from hours of angst.  If you know how to solve this then please edit the wiki.

---

### Post by abtabt on 2015-11-05
> **Jacob_Ritorto said:**
> yes, I did try the yaboot parameters recommended.  nomodeset, offb=off, video=ofonly, each separately.  No affect on the X11 virtual console (though I did see different text-mode character renderings, so it seems that the parameters did affect _something_).

So, abtabt, you think it's just not getting a legit scan rate to satisfy the analog stuff in the crt, then?   I'll try hooking up an external multisync-style screen to the vga port.. 

  I've used regular X more than Xorg, so I have a bit of a learning curve, here, especially now that there's this xorg.d heirarchy thing.  Will Xorg find my conf file, like in the days of yore, if I simply place my custom xorg.conf in /etc/?  

  Did you think that the autosized scan rates that Xorg decided upon in my logfile were bad?

OK, quick update: I hooked up a 17" Apple Studio Display (appears to be a nice multisync Trinitron CRT) to the iMac's built-in VGA port and I'm getting perfect X display with the standard 14.04.2 ppc desktop install distro.  So my whole poor experience in this thread comes down to just a problem with the iMac's built-in display stuff (or misconfigured Xorg, if you want to look at it from the software perspective).  Does anyone know the proper sync stuff to make this tube happy? If not, I'll experiment and report back my findings.  

 This exercise should probably result in some Xorg config conditionals in the new 16.04 release so others don't experience these confusing black screens in the futur/e.  I'm happy to help with the code if somebody can hold my hand through the ubuntu upstream process a little -- while I'm quite familiar with lots of unix dev, git, c, etc., this would be my first serious foray into ubuntu development.

you can get get build in crt to work, one way is like this( its a way to use  live CD )

start in single mod 
when promt
 
Xorg -configure

that give you a xorg.conf.new

edit the file 

nano xorg.conf.new

change  driver  to fbdev  and add DefaultDepth 16

>         #Option     "RenderAccel"               # [<bool>]
        Identifier  "Card0"
        Driver      "fbdev"          #########CHANGE 
        BusID       "PCI:0:16:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"

        Monitor    "Monitor0"
        DefaultDepth 16     ###########ADD THIS 
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
      
cp xorg.conf.new /etc/X11/xorg.conf

and ctrl d   ( to leave single mod and continue boot )

and then you can lab with r128 driver thats a other storry
sorry for my school english

i am running ubuntu-mate 15.10 on imac 500

---

### Post by Jacob_Ritorto on 2015-11-13
It turned out that I did just need an xorg.conf file.  Turns out my little blue g3/400 was able to support 24-bit graphics.  I only needed to provide appropriate sync rates as documented in [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F)  Thanks again for the push in the right direction.

---

