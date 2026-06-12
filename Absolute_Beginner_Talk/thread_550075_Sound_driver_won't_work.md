---
title: "Sound driver won't work"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by smmalis on 2007-09-13
I downloaded the sound driver from Asus' website and tried to install it by running the automatic installer.  The readme says to run ./install.  So I do but it never works.  I still have no sound.  I have an Asus M2V motherboard and would like sound.  Please help!

---

### Post by startherepodcast on 2007-09-13
Hey,

could you please run:

```
./install
```

in a terminal and post the output.

Thanks

Startherepodcast

---

### Post by overdrank on 2007-09-13
> **smmalis said:**
> I downloaded the sound driver from Asus' website and tried to install it by running the automatic installer.  The readme says to run ./install.  So I do but it never works.  I still have no sound.  I have an Asus M2V motherboard and would like sound.  Please help!

Hi can you post the out put of the command in the terminal 
```
lspci
```
The terminal is located under applications, accessories, terminal and this will allow us to identify your sound card and then maybe we can help.

Edit or what is suggested in the first post by Startherepodcast

---

### Post by smmalis on 2007-09-13
The output of lspci is:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. VT3351 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6238
00:00.7 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)
04:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
06:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6121 (rev b1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

The output of ./install is(just the end part, it is too long):
```

/bin/bash ../mkinstalldirs /usr/sbin
/usr/bin/install -c alsactl /usr/sbin/alsactl
/usr/bin/install: cannot remove `/usr/sbin/alsactl': Permission denied
make[2]: *** [install-sbinPROGRAMS] Error 1
make[2]: Leaving directory `/home/steven/Desktop/Linux_Audio/alsa-utils-1.0.9a/alsactl'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/steven/Desktop/Linux_Audio/alsa-utils-1.0.9a/alsactl'
make: *** [install-recursive] Error 1
cp: cannot create link `/usr/lib64/libasound.la': File exists
cp: cannot create link `/usr/lib64/libasound.so': File exists
cp: cannot create link `/usr/lib64/libasound.so.2': File exists
cp: cannot create link `/usr/lib64/libasound.so.2.0.0': File exists
rm: cannot remove `/dev/sndstat': Permission denied
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists
bzip2: Can't open input file test.wav.bz2: No such file or directory.
cp: cannot stat `test.wav': No such file or directory
Remove Folder.....
You must be root to use this script.

```

---

### Post by Terl on 2007-09-13
Have you run the ./install by using sudo?  The last line of the output says you need to be root so you should try sudo ./install

---

### Post by smmalis on 2007-09-13
Tried that just now.  I get into alsaconf, but it doesn't detect my sound chip.  Also, some error messages still spewed into the console:
```
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
cp: cannot create link `/usr/lib64/libasound.la': File exists
cp: cannot create link `/usr/lib64/libasound.so': File exists
cp: cannot create link `/usr/lib64/libasound.so.2': File exists
cp: cannot create link `/usr/lib64/libasound.so.2.0.0': File exists
bzip2: Can't open input file test.wav.bz2: No such file or directory.
cp: cannot stat `test.wav': No such file or directory
Remove Folder.....
modinfo: could not find module snd
modinfo: could not find module snd
modinfo: could not find module snd
modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8

```

---

