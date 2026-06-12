---
title: "Installing nvidia old nv driver on ppc"
date: 2017-07-31
forum: Apple Hardware Users
---

### Post by lucas-weteling on 2017-07-31
Hello,
I have a problem with installing Ubuntu on a old White Half Sphere iMac G4. The problem (for now) is the Nvidia card  [GeForce2 MX/MX 400].
I have installed Ubuntu 14.04.5 LTS (GNU/Linux 3.13.0-125-powerpc-smp ppc) with option lubuntu minimum. Boot gives a dark screen.
So I boot with yaboot: I use "Linux nomodeset single" to get the prompt.

I've read that the problem is the driver nouveau and I had to replace driver nouveau with the old driver nv.

On devtalk.nvidia.com they have found the old nv driver : [https://www.phoronix.com/scan.php?page=news_item&px=X.Org-1.19-Old-Driver-Updates](https://www.phoronix.com/scan.php?page=news_item&px=X.Org-1.19-Old-Driver-Updates)

I'm trying to install the driver xf86-video-nv-2.1.21
I am using the instruction, says: ./configure
The error is:
```

checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XV is defined... no
checking if DPMSExtension is defined... no
checking for XORG... no
configure: error: Package requirements (xorg-server >= 1.3 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
lucas@lucas-ubu-bol:~/xf86-video-nv-2.1.21$ 

```
In environment the path  is
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/games:/usr/bin/:/usr/share/bash-completion/completions:"

While 
$ locate pkg-config
/usr/share/bash-completion/completions/pkg-config
I added the path to the PATH= in the file  /etc/environment

I think I have to edit the file configure, to set XORG_CFLAGS and XORG_LIBS, but I don't know where and how.
Maybe someone knows how.

Regards,
Lucas

---

### Post by QIII on 2017-07-31
Moved to Apple Hardware Users for a better fit.

---

### Post by abtabt on 2017-08-01
hi driver nvidiafb is the only driver from 14.04 and forward (for this card) search in forum if you need  howto

---

### Post by lucas-weteling on 2017-08-04
Thank you for this useful remark. I'm trying it now. I've a cursor on the screen, that's a big step for me.;)

---

### Post by abtabt on 2017-08-05
Its a start i hope you get a GUI 
If not .let.me.now  its easy too get lost to enable nvidiafb etc

---

### Post by lucas-weteling on 2017-08-07
Hi, Yes I have a GUI, a dark screen with a blurred cursor. I can move the cursor.
With:
 sudo /etc/init.d/lightdm stop
the screen is completely black and with
sudo /etc/init.d/lightdm start
the dark screen and the blurred cursor are back again.
Regards, Lucas

---

### Post by abtabt on 2017-08-07
hi if you search posts i have written before, then you can find some answer about i belive your problem

if you use live cd/dvd this is one howto get GUI with desktop (and this must be done if you install the system )


short version

boot option live nomodeset video=offb:off single (when installed it will be Linux nomodeset video=offb:off single ,when all ok remove single  )

wait (black screen you dont see anyting )

then when boot is ended (ca 5min depend of speed )

press enter key

type modprobe nvidiafb  press enter key (you will see CLI if not try one more time  ) (when installed system you must unhash nvidiafb in the blacklist and load nvidiafb)

make a xorg.conf

type Xorg -configure

edit xorg.confnew 

Hash driver and add DefaultDepth 16

cp xorg.confnew /etc/X11/xorg.conf 

then ctrl+D (exit and continue boot and if all is ok you will have GUI with desktop )

and install or test


you can try 16.04 Lubuntu live CD/DVD insted and follow this howto

---

### Post by abtabt on 2017-08-07
Hi 
post the log for X-server       ( Xorg.0.log)

/var/log/Xorg.0.log

---

### Post by lucas-weteling on 2017-08-09
[URL="https://ubuntuforums.org/member.php?u=161416"]**[COLOR=#000000][/COLOR]**[COLOR=#000000]Hi abtabt,


[/COLOR][COLOR=#000000][/COLOR][/URL]It did not work, unfortunately.
I maked the following steps:
1)  new installed ubuntu-ppc
Ubuntu 14.04.5 LTS (GNU/Linux 3.13.0-126-powerpc-smp ppc
Kernel command line: root=UUID=8573e814-a5fa-40de-8755-e1d95ae8f60d ro quiet splash nomodeset video=offonly (video=offb:off was not working)

2) modprobe nvidiafb
controlles with lsmod driver nvidiafb was loaded
 nano /etc/modprobe.d/blacklist.conf has no nvidiafb , so no changes

3)  Xorg -configure
editing xorg.conf.new
Hash driver and add DefaultDepth 16
#Driver      "nouveau"
and in section 
ection "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 16

cp xorg.confnew /etc/X11/xorg.conf

4) reboot
No GUI, it is apity.
What's my mistake?
Regards, Lucas

---

### Post by lucas-weteling on 2017-08-09
Hi,
The /var/log/Xorg.0.log is:
```
[    47.219] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    47.219] X Protocol Version 11, Revision 0
[    47.219] Build Operating System: Linux 4.4.0-83-powerpc64-smp ppc Ubuntu
[    47.232] Current Operating System: Linux lucas-ubu-bol 3.13.0-126-powerpc-smp #175-Ubuntu SMP Thu Jul 20 17:30:26 UTC 2017 ppc
[    47.232] Kernel command line: root=UUID=8573e814-a5fa-40de-8755-e1d95ae8f60d ro quiet splash nomodeset video=offonly 
[    47.233] Build Date: 20 July 2017  07:12:47PM
[    47.233] xorg-server 2:1.15.1-0ubuntu2.9 (For technical support please see http://www.ubuntu.com/support) 
[    47.233] Current version of pixman: 0.30.2
[    47.233]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    47.233] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    47.234] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug  9 22:46:08 2017
[    47.235] (==) Using config file: "/etc/X11/xorg.conf"
[    47.235] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    47.283] (==) ServerLayout "X.org Configured"
[    47.283] (**) |-->Screen "Screen0" (0)
[    47.283] (**) |   |-->Monitor "Monitor0"
[    47.285] (**) |   |-->Device "Card0"
[    47.285] (**) |-->Input Device "Mouse0"
[    47.285] (**) |-->Input Device "Keyboard0"
[    47.285] (==) Automatically adding devices
[    47.285] (==) Automatically enabling devices
[    47.285] (==) Automatically adding GPU devices
[    47.285] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    47.285]     Entry deleted from font path.
[    47.285] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    47.286]     Entry deleted from font path.
[    47.286] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    47.286] (**) ModulePath set to "/usr/lib/xorg/modules"
[    47.286] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    47.286] (WW) Disabling Mouse0
[    47.286] (WW) Disabling Keyboard0
[    47.287] (II) Loader magic: 0x204aa694
[    47.287] (II) Module ABI versions:
[    47.287]     X.Org ANSI C Emulation: 0.4
[    47.287]     X.Org Video Driver: 15.0
[    47.287]     X.Org XInput driver : 20.0
[    47.287]     X.Org Server Extension : 8.0
[    47.315] (--) PCI:*(0:0:16:0) 10de:0110:0000:0000 rev 178, Mem @ 0x91000000/16777216, 0x98000000/134217728, BIOS @ 0x????????/65536
[    47.331] Initializing built-in extension Generic Event Extension
[    47.331] Initializing built-in extension SHAPE
[    47.331] Initializing built-in extension MIT-SHM
[    47.331] Initializing built-in extension XInputExtension
[    47.331] Initializing built-in extension XTEST
[    47.331] Initializing built-in extension BIG-REQUESTS
[    47.331] Initializing built-in extension SYNC
[    47.331] Initializing built-in extension XKEYBOARD
[    47.331] Initializing built-in extension XC-MISC
[    47.336] Initializing built-in extension SECURITY
[    47.337] Initializing built-in extension XINERAMA
[    47.337] Initializing built-in extension XFIXES
[    47.337] Initializing built-in extension RENDER
[    47.337] Initializing built-in extension RANDR
[    47.337] Initializing built-in extension COMPOSITE
[    47.337] Initializing built-in extension DAMAGE
[    47.337] Initializing built-in extension MIT-SCREEN-SAVER
[    47.337] Initializing built-in extension DOUBLE-BUFFER
[    47.337] Initializing built-in extension RECORD
[    47.337] Initializing built-in extension DPMS
[    47.337] Initializing built-in extension Present
[    47.337] Initializing built-in extension DRI3
[    47.337] Initializing built-in extension X-Resource
[    47.337] Initializing built-in extension XVideo
[    47.337] Initializing built-in extension XVideo-MotionCompensation
[    47.337] Initializing built-in extension SELinux
[    47.337] Initializing built-in extension XFree86-VidModeExtension
[    47.337] Initializing built-in extension XFree86-DGA
[    47.337] Initializing built-in extension XFree86-DRI
[    47.337] Initializing built-in extension DRI2
[    47.338] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    47.338] (WW) "xmir" is not to be loaded by default. Skipping.
[    47.338] (II) LoadModule: "glx"
[    47.339] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    47.741] (II) Module glx: vendor="X.Org Foundation"
[    47.786]     compiled for 1.15.1, module version = 1.0.0
[    47.786]     ABI class: X.Org Server Extension, version 8.0
[    47.786] (==) AIGLX enabled
[    47.786] Loading extension GLX
[    47.787] (II) LoadModule: "nvidiafb"
[    47.843] (WW) Warning, couldn't open module nvidiafb
[    47.844] (II) UnloadModule: "nvidiafb"
[    47.844] (II) Unloading nvidiafb
[    47.844] (EE) Failed to load module "nvidiafb" (module does not exist, 0)
[    47.844] (==) Matched nvidia as autoconfigured driver 0
[    47.844] (==) Matched nouveau as autoconfigured driver 1
[    47.844] (==) Matched modesetting as autoconfigured driver 2
[    47.844] (==) Matched fbdev as autoconfigured driver 3
[    47.845] (==) Assigned the driver to the xf86ConfigLayout
[    47.845] (II) LoadModule: "nvidia"
[    47.846] (WW) Warning, couldn't open module nvidia
[    47.846] (II) UnloadModule: "nvidia"
[    47.846] (II) Unloading nvidia
[    47.846] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    47.846] (II) LoadModule: "nouveau"
[    47.847] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    47.913] (II) Module nouveau: vendor="X.Org Foundation"
[    47.913]     compiled for 1.15.0, module version = 1.0.10
[    47.913]     Module class: X.Org Video Driver
[    47.913]     ABI class: X.Org Video Driver, version 15.0
[    47.914] (II) LoadModule: "modesetting"
[    47.915] (WW) Warning, couldn't open module modesetting
[    47.915] (II) UnloadModule: "modesetting"
[    47.915] (II) Unloading modesetting
[    47.915] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    47.915] (II) LoadModule: "fbdev"
[    47.919] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    47.934] (II) Module fbdev: vendor="X.Org Foundation"
[    47.934]     compiled for 1.15.0, module version = 0.4.4
[    47.934]     Module class: X.Org Video Driver
[    47.934]     ABI class: X.Org Video Driver, version 15.0
[    47.934] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    47.934] (II) NOUVEAU driver for NVIDIA chipset families :
[    47.934]     RIVA TNT        (NV04)
[    47.934]     RIVA TNT2       (NV05)
[    47.935]     GeForce 256     (NV10)
[    47.935]     GeForce 2       (NV11, NV15)
[    47.935]     GeForce 4MX     (NV17, NV18)
[    47.935]     GeForce 3       (NV20)
[    47.935]     GeForce 4Ti     (NV25, NV28)
[    47.951]     GeForce FX      (NV3x)
[    47.951]     GeForce 6       (NV4x)
[    47.951]     GeForce 7       (G7x)
[    47.951]     GeForce 8       (G8x)
[    47.951]     GeForce GTX 200 (NVA0)
[    47.951]     GeForce GTX 400 (NVC0)
[    47.956] (II) FBDEV: driver for framebuffer: fbdev
[    47.956] (++) using VT number 7

[    47.957] (EE) [drm] KMS not enabled
[    47.958] (II) Loading sub module "fbdevhw"
[    47.958] (II) LoadModule: "fbdevhw"
[    47.958] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    47.959] (II) Module fbdevhw: vendor="X.Org Foundation"
[    47.959]     compiled for 1.15.1, module version = 0.0.2
[    47.959]     ABI class: X.Org Video Driver, version 15.0
[    47.962] (**) FBDEV(0): claimed PCI slot 0@0:16:0
[    47.962] (II) FBDEV(0): using default device
[    47.963] (**) FBDEV(0): Depth 16, (--) framebuffer bpp 16
[    47.963] (==) FBDEV(0): RGB weight 565
[    47.963] (==) FBDEV(0): Default visual is TrueColor
[    47.963] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    47.963] (II) FBDEV(0): hardware: OFfb NVDA,NVMac (video memory: 768kB)
[    47.977] (II) FBDEV(0): checking modes against framebuffer device...
[    47.978] (II) FBDEV(0): checking modes against monitor...
[    47.978] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    47.978] (**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 94.0 kHz, 116.3 Hz
[    47.978] (II) FBDEV(0): Modeline "current"x0.0  100.00  1024 1040 1048 1064  768 784 792 808 -hsync -vsync -csync (94.0 kHz b)
[    47.978] (==) FBDEV(0): DPI set to (96, 96)
[    47.978] (II) Loading sub module "fb"
[    47.978] (II) LoadModule: "fb"
[    47.979] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.979] (II) Module fb: vendor="X.Org Foundation"
[    47.987]     compiled for 1.15.1, module version = 1.0.0
[    47.987]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.987] (**) FBDEV(0): using shadow framebuffer
[    47.987] (II) Loading sub module "shadow"
[    47.987] (II) LoadModule: "shadow"
[    47.988] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    47.989] (II) Module shadow: vendor="X.Org Foundation"
[    47.989]     compiled for 1.15.1, module version = 1.1.0
[    47.989]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.990] (EE) FBDEV(0): FBIOPUT_VSCREENINFO succeeded but modified mode
[    47.990] (EE) FBDEV(0): mode initialization failed
[    47.990] (EE) 
Fatal server error:
[    47.990] (EE) AddScreen/ScreenInit failed for driver 0
[    47.990] (EE) 
[    47.990] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    47.990] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    47.991] (EE) 
[    48.032] (EE) Server terminated with error (1). Closing log file.
```
Regards,
Lucas

---

### Post by abtabt on 2017-08-10
Hi i see in log row 47.963 this is a problem the nouvue framebuffer is active NOG nvidiafb 
Video=offb:off disable nouvue framebuffer etc .and Blacklist have a file with nvidiafb blacklist-framebuffer.conf and fbdev-blacklist.conf ,have you change this File to unblock nvidiafb ?
 
If you can ,download live CD lubuntu 16.04 and try its easy too get working, no need edit Blacklist etc

And i will be home later this week ,dont give upp

---

### Post by lucas-weteling on 2017-08-10
Haha, I will download live CD lubuntu 16.04, I (we) don't give up!!
Tank you for the support.
Regards,

Lucas

---

### Post by abtabt on 2017-08-10
> **lucas-weteling said:**
> Haha, I will download live CD lubuntu 16.04, I (we) don't give up!!
Tank you for the support.
Regards,

Lucas
Thats right move on

When you have download lubuntu 

At the yaboot prompt type: 

Code:
live video=offb:off nomodeset single
This will freeze or give you a blank screen. You will have to judge blind when the machine has finished booting which can be LONGER than you think
 
Press Enter key once

 the command (you won't see what you type)

Code:
modprobe nvidiafb mode_option=1024x768-16
 
The text should now appear on the screen.

If it doesn't  try One more time  if no text then type

Code:
modprobe nvidiafb (this give you 8 bit and need a xorg.conf File to Grease to 16,24 bit)
You can start the desktop with 

Ctrl key + D

---

### Post by lucas-weteling on 2017-08-11
Hi Atbabt,

Of course I downloaded Lubuntu 16.04 live
Started boot dvd:
Live nomoset video=offb:off single
Modprobe nvidiafb

Command Line appeared

Xorg configuration
Nano xorg.conf.new

Hash driver and add DefaultDepth 16
Cp xorg.conf.new /etc/X11/xorg.conf

<Ctrl> + D
And the GUI appeared (Hurray)

I tested a little bit and then I've installed Lubuntu 16.04
After installing Reboot
No GUI, no cli

Then I saw your new message
So a second attempt following the instructions of the new message
live video=offb:off nomodeset single

modprobe nvidiafb mode_option=1024x768-16
Ctrl key + D 
GUI appeared (Hurray, again)
Installing Lubuntu
...
Reboot
Linux nomoset video=offb:off single 
No GUI no cli
Reboot
no GUI no cli

Regards, Lucas

---

### Post by abtabt on 2017-08-11
This is ok then we now X working 
 edit Blacklist hash nvidiafb 
edit yaboot file and remove single etc
and you need the xorg.conf in place
/etc/X11/xorg.conf


We are at finish line

edit  

 sudo nano /etc/modprobe.d/blacklist-framebuffer.conf 

 ```
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist bochs-drm
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
#blacklist nvidiafb   [COLOR="#FF0000"]<<<<<<< HASH THIS LINE[/COLOR]
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb#blacklist nvidiafb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
#blacklist vesafb
blacklist vfb
blacklist viafb
blacklist vt8623fb
blacklist udlfb

```

edit 

sudo nano /etc/yaboot.conf

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ata-ST3200822A_4LJ0SPM2-part14"
device=/pci@f2000000/mac-io@17/ata-4@1f000/@0
partition=13
root="UUID=19a6eb9c-caf6-42fd-b818-f51f81328b8f"
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx="/dev/disk/by-id/ata-ST3200822A_4LJ0SPM2-part10"

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="nomodeset video=offb:off"                [COLOR="#FF0000"] <<<<<<<<<<<<<<< LIKE THIS[/COLOR]

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="nomodeset video=offb:off"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda15.
image=/pci@f2000000/mac-io@17/ata-4@1f000/@0:15,/boot/vmlinux
    label=Ubuntu-Linux
    root="UUID=9641736e-0570-4954-98d9-106b4ef84db4"
    append=" ro nomodeset video=offb:off"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/@0:15,/boot/initrd.img

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda15.
image=/pci@f2000000/mac-io@17/ata-4@1f000/@0:15,/boot/vmlinux.old
    label=Ubuntu-old
    root="UUID=9641736e-0570-4954-98d9-106b4ef84db4"
    append=" ro nomodeset video=offb:off"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/@0:15,/boot/initrd.img.old

```

and then 

```
sudo ybin -v
```

and reboot this shuld be all for a working system GUI with desktop

some tweaks i do is swappines 10 ,disable crash report , blacklist some modules and install htop if you want to see CPU , MEMORY LOAD ,KILL things etc

---

### Post by lucas-weteling on 2017-08-12
Hello Atbabt,

It's working!!
Thank you very much.
Douze points! That's twelve points on a scale of 0 to 10.

Best Regards,
Lucas

---

