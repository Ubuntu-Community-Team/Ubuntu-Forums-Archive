---
title: "Mac Pro Late 2013 Fatal Crash to Black Screen, Syslog Spits GPU &amp; CPU-related Issues"
date: 2019-01-27
forum: Apple Hardware Users
---

### Post by mjanik on 2019-01-27
Hey all!

Long time Linux user, fairly new forum poster.

_**System**_

Currently running Kubuntu 18.04 (along with macOS and Windows) on my Late 2013 Mac Pro6,1: 

[https://support.apple.com/kb/SP697?locale=en_US](https://support.apple.com/kb/SP697?locale=en_US)
**Processor** - Intel Xeon E5 with 25MB L3 cache and Turbo Boost up to 3.9GHz - 3.0GHz 8-Core
**Memory** - DDR3 ECC memory 3.0GHz 8-Core 64GB (four 16GB)
**Graphics** - Dual AMD FirePro D300 graphics processors with 2GB of GDDR5 VRAM each - 3.7GHz Quad-Core

_**Problem**_

Everything actually runs really well! I'm just plagued with this crazy random crash that stops me from using Kubuntu for too long. Basically as the title says, everything "on the outside" stops responding: display goes black, keyboard/mouse unresponsive, power button no use.

**Causes and symptoms**

Usage - Use Kubuntu for anywhere between 0 to 24 hours (or more for all I know)
Usage - Usually be doing something super important (as is my luck), or not
CRASH > on the surface - Screen goes black, peripherals unresponsive, single press of power button shows nothing (hold does a hard reset)
CRASH > in the background - The system seems to continue to log to syslog for a time (thankfully), so that tells me the kernel didn't panic?

[**Here's an Ubuntu pastebin**]("https://paste.ubuntu.com/p/BnJ8t35VDp/") of the **lspci** command, and **the syslog  **(because it's too big of a .txt file to attach...) from the moment of the crash, when I try and press the power button once, then when I hard reset and boot Kubuntu back up. There are loads of radeon errors in there, among other errors. Answers probably in there, and probably as simple as "Sorry, your card(s) isn't/aren't supported."

**Update:** Happened a few more times. [**Here's another Ubuntu pastebin of the crash**]("https://paste.ubuntu.com/p/HCPWNGGTsq/"). Crash logging starts at line 70 in this one. This time I tried unplugging and plugging my keyboard back in while the screen was black. Syslog seemed to show it happening (lines 205-217), so there's something weird going on. The first  line of the crash always seems to be:
```
Jan 27 20:16:54 kubuntu18 kernel: [  415.474319] pciehp 0000:00:03.0:pcie004: Slot(5-3): Link Down
```
PCI 00:03.0 is the third 'root port' of my CPU. Not sure if slot 5-3 is something that's connected to those slots? Maybe GPU? or just the CPU itself? 
Lines 92-102 seem pretty telling. PCE 00:06:00.0 is one of my GPUs, and it seems the radeon driver is having some trouble dealing with whatever is going on. Log says GPU lockup at line 96.
```
Jan 27 20:16:59 kubuntu18 kernel: [  420.621819] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Jan 27 20:16:59 kubuntu18 kernel: [  420.621851] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing D09C (len 75, WS 0, PS 0) @ 0xD0CB
Jan 27 20:17:01 kubuntu18 CRON[3849]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 27 20:17:04 kubuntu18 kernel: [  425.574895] radeon 0000:06:00.0: ring 0 stalled for more than 10152msec
Line 96 > Jan 27 20:17:04 kubuntu18 kernel: [  425.574905] radeon 0000:06:00.0: GPU lockup (current fence id 0x0000000000003cc6 last fence id 0x0000000000003ccd on ring 0)
Jan 27 20:17:04 kubuntu18 kernel: [  425.625910] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Jan 27 20:17:04 kubuntu18 kernel: [  425.625941] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing D0E8 (len 62, WS 0, PS 0) @ 0xD104
Jan 27 20:17:05 kubuntu18 kernel: [  426.519799] BUG: unable to handle kernel paging request at ffffc0fac7325ffc
Jan 27 20:17:05 kubuntu18 kernel: [  426.519848] IP: radeon_ring_backup+0xd3/0x140 [radeon]
Jan 27 20:17:05 kubuntu18 kernel: [  426.519852] PGD 103ed48067 P4D 103ed48067 PUD 0 
Jan 27 20:17:05 kubuntu18 kernel: [  426.519859] Oops: 0000 [#1] SMP PTI
```

I also posted a bit more (more syslog, code output) to the Kubuntu forums, but that's not going too well:
[https://www.kubuntuforums.net/showthread.php/75015-Consistent-but-random-fatal-crashes-requiring-a-hard-reset](https://www.kubuntuforums.net/showthread.php/75015-Consistent-but-random-fatal-crashes-requiring-a-hard-reset)
I also have searched around here for solutions, but all the Mac Pro issues seem to be installation-related. The few I came across with this issue didn't have much troubleshooting info at all.

It should be known that my thunderbolt display has also caused me issues, particularly with the "suspend to RAM", but switching to an HDMI display seems to have fixed that! The syslogs I provided above are while using the HDMI display. No thunderbolt devices are plugged into any ports.
It should also be known that this issue has happened a few times while using an Ubuntu (not Kubuntu) 18.04 Live USB, so as far as I can tell it's not solely Kubuntu-related.

Pasted below is a system profile, and lsblk.

inxi -Fxz (System Profile)

```
System:    Host: kubuntu18 Kernel: 4.15.0-43-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: KDE Plasma 5.12.7 (Qt 5.9.5) Distro: Ubuntu 18.04.1 LTS
Machine:   Device: unknown System: Apple product: MacPro6 1 v: 1.0 serial: N/A
           Mobo: Apple model: Mac-F60DEB81FF30ACF6 v: MacPro6 1 serial: N/A
           UEFI: Apple v: 127.0.0.0.0 date: 09/17/2018
CPU:       Quad core Intel Xeon E5-1620 v2 (-MT-MCP-) arch: Ivy Bridge rev.4 cache: 10240 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 29599
           clock speeds: max: 3900 MHz 1: 1795 MHz 2: 1323 MHz 3: 2388 MHz 4: 1303 MHz 5: 1393 MHz 6: 1300 MHz
           7: 1488 MHz 8: 1264 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X]
           bus-ID: 02:00.0
           Card-2: Advanced Micro Devices [AMD/ATI] Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X]
           bus-ID: 06:00.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x1024@60.02hz
           OpenGL: renderer: AMD PITCAIRN (DRM 2.50.0 / 4.15.0-43-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.5 Direct Render: Yes
Audio:     Card-1 Intel C600/X79 series High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 2x Advanced Micro Devices [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
           driver: snd_hda_intelsnd_hda_intel bus-ID: 06:00.1
           Card-3 Focusrite-Novation Scarlett 18i8 driver: USB Audio usb-ID: 002-002
           Sound: Advanced Linux Sound Architecture v: k4.15.0-43-generic
Network:   Card-1: Broadcom Limited NetXtreme BCM57762 Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 0b:00.0
           IF: enp11s0 state: up speed: 100 Mbps duplex: half mac: <filter>
           Card-2: Broadcom Limited NetXtreme BCM57762 Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 0c:00.0
           IF: enp12s0 state: down mac: <filter>
           Card-3: Broadcom Limited BCM4360 802.11ac Wireless Network Adapter driver: wl bus-ID: 0d:00.0
           IF: wlp13s0 state: down mac: <filter>
Drives:    HDD Total Size: 1000.6GB (3.5% used)
           ID-1: /dev/sda model: APPLE_SSD_SM1024 size: 1000.6GB
Partition: ID-1: / size: 47G used: 33G (75%) fs: ext4 dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A gpu: 53.0,52.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 219 Uptime: 48 min Memory: 1197.7/64392.7MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```

lsblk

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   200M  0 part /boot/efi                                                                                               
&#9500;&#9472;sda2   8:2    0 604.7G  0 part      (macOS)                                                                                                        
&#9500;&#9472;sda3   8:3    0  47.8G  0 part /    (Linux)                                                                                                   
&#9492;&#9472;sda4   8:4    0 279.1G  0 part      (Windows)
```

Anyway, hopefully a guru can give me some additional info on whether or not there's anything I can do about this, or if my hardware is simply not supported at this time.

Thanks, all!
All the best.

---

