---
title: "Wine might as well not be installed"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2008-01-13
Darnit i hate wine

So everything i put in wine gives me basically the same thing. I reinstalled the damn thing.

Any command gives me something similar

And i apparantly cant post it because it counts as an image

(90% of the gibbrish is cut out so it lets me post it

> Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at address 0x7e63e889 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000000b8 in 32-bit code (0x7e63e889).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e63e889 ESP:0034ee10 EBP:0034ee38 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:7c02f470 EDX:00000000
 ESI:00000000 EDI:7c03c668

Modules:
Module  Address                 Debug info      Name (42 modules)
PE        400000-  414000       Deferred        setupaudiosurf_betaweekend1_1.11Z:\home\ryan\Desktop\SetupAudiosurf_BetaWeekend1_1.11.08.exe
PE      65340000-653d2000       Deferred        oleaut32
PE      65f00000-65fc2000       Deferred        ole32
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e5de000-7e5e8000       Deferred        libdrm.so.2
ELF     7e5e8000-7e819000       Export          r300_dri.so
ELF     7e819000-7e8a3000       Export          libgl.so.1
ELF     7e8a3000-7e8a8000       Deferred        libxdmcp.so.6
ELF     7e8a8000-7e8ab000       Deferred        libxau.so.6
ELF     7e8ab000-7e99c000       Deferred        libx11.so.6
ELF     7e99c000-7e9aa000       Deferred        libxext.so.6
ELF     7e9aa000-7e9af000       Deferred        libxxf86vm.so.1
ELF     7e9af000-7e9c7000       Deferred        libice.so.6
ELF     7e9c7000-7e9cf000       Deferred        libsm.so.6
ELF     7e9df000-7ea6a000       Dwarf           winex11<elf>
  \-PE  7e9f0000-7ea6a000       \               winex11
ELF     7eabf000-7eadf000       Deferred        libexpat.so.1
ELF     7eadf000-7eb0a000       Deferred        libfontconfig.so.1
ELF     7eb0a000-7eb1f000       Deferred        libz.so.1
ELF     7eb1f000-7eb8f000       Deferred        libfreetype.so.6
ELF     7eb9f000-7ec5d000       Deferred        comctl32<elf>
  \-PE  7ebb0000-7ec5d000       \               comctl32
ELF     7ec5d000-7eca6000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca6000       \               advapi32
ELF     7eca6000-7ed41000       Dwarf           gdi32<elf>
  \-PE  7ecc0000-7ed41000       \               gdi32
ELF     7ed41000-7ee7f000       Dwarf           user32<elf>
  \-PE  7ed60000-7ee7f000       \               user32
ELF     7ef9e000-7efa9000       Deferred        libnss_files.so.2
ELF     7efa9000-7efb3000       Deferred        libnss_nis.so.2
ELF     7efb3000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff0000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d18000-b7d1c000       Deferred        libdl.so.2
ELF     b7d1c000-b7e66000       Deferred        libc.so.6
ELF     b7e67000-b7e7f000       Deferred        libpthread.so.0
ELF     b7e8f000-b7fa3000       Dwarf           libwine.so.1
ELF     b7fa5000-b7fc1000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\ryan\Desktop\SetupAudiosurf_BetaWeekend1_1.11.08.exe
        00000009    0 <==
ryan@ryan-desktop:~$ 


i tried reinstalling, but the bloody thing is useless. Anything i try to do in wine under applications does not respond.

Anyone wanna help?

---

### Post by thelatinist on 2008-01-13
Well, the "gibberish" seems to indicate a graphics driver problem.  You have an ATI graphics card, but it would help to know what chipset it uses and what drivers you are using.

Please post the output of the following command:

```
lspci
```

Also, are you using the open source ATI drivers, or the restricted binaries?

---

### Post by nikoPSK on 2008-01-13
Try fooling around in the config. :)

```
winecfg
```

nikoPSK

---

### Post by Toxicity999 on 2008-01-13
Broken Graphics drivers.

---

### Post by nikoPSK on 2008-01-13
> **Toxicity999 said:**
> Broken Graphics drivers.

most likely, if that is the case you could reconfigure xorg, or just reinstall them :)

---

### Post by thedrizz on 2008-01-13
> 00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801ER (ICH5R) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT]
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)
02:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:03.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
ryan@ryan-desktop:~$ 


Reinstall and winecfg dont work :(

compiz works on this, so why wont wine??!

---

### Post by thelatinist on 2008-01-13
So you have a Radeon9800 with a Rage 350 chipset.  First step.

Now, do you have the restricted drivers installed, or are you using the default open source ones?

---

### Post by thedrizz on 2008-01-13
> **thelatinist said:**
> So you have a Radeon9800 with a Rage 350 chipset.  First step.

Now, do you have the restricted drivers installed, or are you using the default open source ones?

i have the restricted drivers

> 
Section "Device"
	Identifier	"ATI Technologies Inc RV350 NJ [Radeon 9800 XT]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

or at least they were the restricted drivers. 

Whats the setting for the correct driver? Unless something crazy happened, i know its installed

---

### Post by thelatinist on 2008-01-13
Try this:

```
sudo apt-get update
sudo apt-get --reinstall install linux-restricted-modules-generic restricted-manager

```

Go to System -> Administration -> Restricted Drivers Manager and choose "ATI accelerated graphics driver"

Restart.

---

### Post by moffa on 2008-01-13
I believe the proprietary drivers are named fglrx while the open source drivers are named 'ati'.  Please try re-installing the proprietary drivers.

---

### Post by nikoPSK on 2008-01-13
> **thedrizz said:**
> i have the restricted drivers



or at least they were the restricted drivers. 

Whats the setting for the correct driver? Unless something crazy happened, i know its installed

If something crazy *did *happen, do this please
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by thelatinist on 2008-01-13
> **nikoPSK said:**
> If something crazy *did *happen, do this please
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

This was going to be my next suggestion after reinstalling the drivers.

---

### Post by nikoPSK on 2008-01-13
> **thelatinist said:**
> This was going to be my next suggestion after reinstalling the drivers.

Hehe, it's fine, we all benefit. :p

nikoPSK

---

### Post by thedrizz on 2008-01-13
er that gave me the problem i had in this thread

[http://ubuntuforums.org/showthread.php?t=597532](http://ubuntuforums.org/showthread.php?t=597532)

i'm going to use the same solution, but that avenue clearly doesnt work

---

### Post by nikoPSK on 2008-01-13
> **thedrizz said:**
> er that gave me the problem i had in this thread

[http://ubuntuforums.org/showthread.php?t=597532](http://ubuntuforums.org/showthread.php?t=597532)

i'm going to use the same solution, but that avenue clearly doesnt work

it shouldn't.... :confused:

---

### Post by thedrizz on 2008-01-13
> **nikoPSK said:**
> it shouldn't.... :confused:

Ok, got ubuntu showing the screen again

the accelerated drivers are not on, nor do i want to turn them on. Is there another option

---

### Post by nikoPSK on 2008-01-13
does 

```
startx
```

work?

---

### Post by thedrizz on 2008-01-13
er, wine is working, but compiz isnt.

*sigh*

---

### Post by nikoPSK on 2008-01-13
well, does this work?

```
compiz --replace
```

---

### Post by thedrizz on 2008-01-31
i got compiz working by reinstalling the official ATI drivers for linux.

Now wine doesnt work again.

Is there no happy medium for poor me?!

---

### Post by nikoPSK on 2008-02-01
> **thedrizz said:**
> i got compiz working by reinstalling the official ATI drivers for linux.
 
Now wine doesnt work again.
 
Is there no happy medium for poor me?!
 
so output of wine from terminal please?

---

### Post by thedrizz on 2008-02-01
just typing wine?

Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

but otherwise, the same as it was in the begining of the thread

---

### Post by Nythain on 2008-02-01
> **thedrizz said:**
> Is there no happy medium for poor me?!
Dual boot for all windows needs??? or use native linux apps??? either way, ditch wine???

---

### Post by nikoPSK on 2008-02-02
> **Nythain said:**
> Dual boot for all windows needs??? or use native linux apps??? either way, ditch wine???

Just wait for now, don't get the chap too confused. :)

---

### Post by thedrizz on 2008-03-19
argh is there another wine-like program that doesn't cost $50 a year? This lack of wine is killing me

---

