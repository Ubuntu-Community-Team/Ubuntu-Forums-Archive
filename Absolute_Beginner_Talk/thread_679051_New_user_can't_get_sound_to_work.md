---
title: "New user can't get sound to work"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by billnj on 2008-01-26
I have wanted to load up Ubuntu and try it for a long time.  Last week I salvaged our old Gateway 450 from the scrap pile and loaded up Gutsy 7.10 and and I am having a lot of fun with it.

Unfortunately, I am having a major problem with sound.  I can't get a peep out of my computer.  I spent a lot of time in the forums following threads about sound and have tried many of the suggested fixes without success.  I used the comprehensive sound guide and  queried my system as it suggested.  Here is the info:

bill@OldGateway:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

______________________________________


bill@OldGateway:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f5000000-f5ffffff
        Prefetchable memory behind bridge: fc000000-fcffffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 1000 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 1020 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Gateway 2000 Tabor2
        Flags: bus master, slow devsel, latency 96, IRQ 11
        I/O ports at 1040 [size=64]
        Capabilities: <access denied>

00:0e.0 Communication controller: 3Com Corp, Modem Division WinModem
        Subsystem: 3Com Corp, Modem Division USR 56k Internal Voice WinModem (Models 2974, 3529)
        Flags: medium devsel, IRQ 11
        Memory at f4020400 (32-bit, prefetchable) [disabled] [size=64]
        Memory at f4030000 (32-bit, prefetchable) [disabled] [size=64K]
        Memory at f4028000 (32-bit, prefetchable) [disabled] [size=32K]
        Capabilities: <access denied>

00:0f.0 Mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/Ultra66) (rev 01)
        Subsystem: Promise Technology, Inc. Ultra66
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 10c0 [size=8]
        I/O ports at 1014 [size=4]
        I/O ports at 1018 [size=8]
        I/O ports at 1010 [size=4]
        I/O ports at 1080 [size=64]
        Memory at f4000000 (32-bit, non-prefetchable) [size=128K]
        Expansion ROM at 20000000 [size=64K]

00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Netgear Unknown device f31d
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 1400 [size=256]
        Memory at f4020000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04) (prog-if 00 [VGA])
        Subsystem: VISIONTEK Unknown device 0020
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Memory at fc000000 (32-bit, prefetchable) [size=16M]
        Capabilities: <access denied>
______________________________________________________

bill@OldGateway:~$ sudo modprobe snd-ens1371
bill@OldGateway:~$ 

________________________________________________________________

It seems to recognize the sound card but I still can't get any sound out of the computer.   CDs seem to be playing when I put them in and the rythymbox player looks like it is working but no sound comes out.  I checked the speakers and they are not muted.  I called up alsamixer from the terminal and made sure that the settings were correct.  Still no luck.  Out of sheer desperation I even ran some command about backchannel something or other that the threads swore works but with no luck.

I am brand new to Linux and anxious to learn.  Pleas bear with me if I don't catch on too quickly.

---

### Post by ynef on 2008-01-26
It is not uncommon for the mixer to have "Master" set to mute. Try running "alsamixer" from the terminal, and you should get a window with a mixer. Hit "m" on any channels that seem to be important (Master, Master M, PCM, etc...) -- in the muted state, they read MM and unmuted they are green OO.

---

### Post by billnj on 2008-01-26
Thanks for the quick reply.  I've already checked out the alsamixer and made sure that all channels are not muted.  Checked it again after your reply and still have no muted channels.

---

### Post by haggus on 2008-01-26
you can open a terminal and 

type sudo alsaconf 


that should bring up the cofiguration utuility just select your sound card and let it configure for you but check the sound settings first.

---

### Post by billnj on 2008-01-26
I typed sudo alsaconf into the terminal and got this reply:  "command not found"

---

### Post by ynef on 2008-01-26
If alsaconf doesn't do anything, could you please post your output of "lsmod" as well? It seems like (at least back in 2004) there was a problem in Debian where several modules were loaded and they clashed, resulting in no sound coming out. [http://lists.debian.org/debian-kde/2004/10/msg00177.html](http://lists.debian.org/debian-kde/2004/10/msg00177.html)

---

### Post by billnj on 2008-01-26
Here is my output from lsmod:

bill@OldGateway:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
apm                    22616  2 
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
lp                     12580  0 
snd_ens1371            28064  1 
gameport               16776  1 snd_ens1371
snd_ac97_codec        102180  1 snd_ens1371
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            53632  0 
snd_mixer_oss          18304  1 snd_pcm_oss
snd_pcm                88836  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11528  1 snd_pcm
snd_seq_oss            35712  0 
snd_seq_midi           10752  0 
snd_rawmidi            27392  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
nvidia               3932108  0 
snd_seq                58608  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26116  2 snd_pcm,snd_seq
snd_seq_device          9740  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usblp                  15104  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd                    64012  15 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_page_alloc,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
psmouse                39952  0 
i2c_piix4               9740  0 
serio_raw               8068  0 
pcspkr                  4224  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
soundcore               8800  1 snd
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
i2c_core               26112  1 i2c_piix4
evdev                  11136  1 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18560  3 
8139too                27776  0 
sg                     36764  0 
sd_mod                 30336  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
pdc202xx_old            9472  0 [permanent]
ide_core              116804  2 ide_disk,pdc202xx_old
uhci_hcd               26640  0 
usbcore               138632  3 usblp,uhci_hcd
ata_piix               17540  0 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sg,sd_mod,sr_mod,libata
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
bill@OldGateway:~$

---

### Post by billnj on 2008-01-26
Can you tell me what to do now?  I'm a bit lost.  I read the post that you directed me to about the two sound drivers conflicting, but I don't know how to fix it.

---

### Post by AutumnPhoenix on 2008-01-27
Using xubuntu and 2-year old thinkpad laptop I was able to fix my sound problem by using the volume controls and toggling my manual mute button until the computer was responsive.  As you're using a desktop I'm sure you have the speakers on so perhaps try a different set of speakers.  Also, make sure that you are testing the sound with something you are able to use, eg, make sure flash is installed if you want to watch an internet video.

---

### Post by xeth_delta on 2008-01-27
Let's see if the modules are loaded properly. Do the following:
```
dmesg | grep -i alsa
```
What is the output?

---

### Post by billnj on 2008-01-27
I tried it twice and I get no response at all:

bill@OldGateway:~$ dmesg | grep -i alsa
bill@OldGateway:~$ 
bill@OldGateway:~$ dmesg | grep -i alsa
bill@OldGateway:~$ 


Should this command have "sudo" in front of it?

Sorry for the complete lack of Linux/Ubuntu knowledge.

---

### Post by maxfeijoada on 2008-01-27
I've got the same problem with my sound board, but when I used Caixa Magica (another linux dist.) my board works fine, but I want to use xubuntu, and I need to install the latest version of alsa drivers. I've downloaded it but I don't know how to install it ( I was a windows user).

---

### Post by xeth_delta on 2008-01-27
> **billnj said:**
> I tried it twice and I get no response at all:

bill@OldGateway:~$ dmesg | grep -i alsa
bill@OldGateway:~$ 
bill@OldGateway:~$ dmesg | grep -i alsa
bill@OldGateway:~$ 


Should this command have "sudo" in front of it?

Sorry for the complete lack of Linux/Ubuntu knowledge.

No need to use sudo for dmesg. Please try:
```
sudo /etc/init.d/alsa-utils restart
```
followed by
```
dmesg
```
post the last lines, or the ones that might relate to the soundcard. If you cannot find any, copy and paste here the output from dmesg. Please do place the output between CODE statements (use the # button in the posting window), otherwise it will be difficult to follow, it should look like this:
```
paste code here
```

---

### Post by xeth_delta on 2008-01-27
> **maxfeijoada said:**
> I've got the same problem with my sound board, but when I used Caixa Magica (another linux dist.) my board works fine, but I want to use xubuntu, and I need to install the latest version of alsa drivers. I've downloaded it but I don't know how to install it ( I was a windows user).

You can follow [URL="http://ubuntuforums.org/showthread.php?t=205449"]this very good guide] (look for the compilation part) or the following steps:

Please note that the method I describe oes not create any deb packages.
The steps you have to take:

download the drivers from: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
You can also get the libraries and utils just to be consistent and have the latest version of them all. For example let's say version 1.0.15

Unpack the three files you just got.
```
cd alsa-lib-1.0.15
./configure
make
sudo make install
```

Make sure you know what card you have:
```
lspci | grep -i audio
```

```
cd alsa-driver-1.0.15
```
You can see available drivers with:
```
./configure --help
```
Configure and make
```
./configure --with-cards=your_card_driver
make
sudo make install
```

```
cd alsa-utils-1.0.15
./configure
make
sudo make install
```

```
sudo alsaconf
```
Follow the instructions. Hopefully now you should also have a /etc/init.d/alsasound or /etc/init.d/alsa script you can use to restart the sound system.

Check if the modules have been loaded with **lsmod**. You should have some atiixp or the like. If not try loading the module with
```
sudo modprobe snd
```
If there are any error messages post the output here.
Do not delete these directories, you will need them should you want to remove the drivers.
Xeth

---

### Post by billnj on 2008-01-29
Thanks for the help.  I will not be able to try these things until the weekend because of my work schedule.  Ubuntu is my new weekend hobby.  I let you know how it works out.

---

### Post by billnj on 2008-02-01
I ran #sudo /etc/init.s/alsa-utils restart# as you suggested.  Then I ran #dmesg#

I didn't recognize a sound card or sound driver so I am posting the output that I copied from the terminal window after I ran #dmesg#.  It is pretty long but here it is:

#bill@OldGateway:~$ sudo /etc/init.d/alsa-utils restart#
[sudo] password for bill:
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 

#bill@OldGateway:~$ dmesg#
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[    0.000000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[    0.000000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000040ffc00 - 0000000018000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 384MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98304) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98304
[    0.000000]   HighMem     98304 ->    98304
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98304
[    0.000000] On node 0 totalpages: 98304
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 736 pages used for memmap
[    0.000000]   Normal zone: 93472 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6AC0 checksum 0
[    0.000000] ACPI: RSDP 000F6AC0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 040FDA87, 0028 (r1 PTLTD    RSDT          0 PTL   1000000)
[    0.000000] ACPI: FACP 040FF78C, 0074 (r1 GATEWA TABOR II 19990422 PTL     F4240)
[    0.000000] ACPI: DSDT 040FDAAF, 1CDD (r1 GATEWA TABOR II        0 MSFT  1000000)
[    0.000000] ACPI: FACS 040FFBC0, 0040
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7fe7000)
[    0.000000] Built 1 zonelists.  Total pages: 97536
[    0.000000] Kernel command line: root=UUID=ee90309a-e372-4fb5-b3c8-eb76d56c6460 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0130c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 448.832 MHz processor.
[   42.971929] Console: colour VGA+ 80x25
[   42.973134] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   42.974376] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   43.033108] Memory: 378248k/393216k available (2015k kernel code, 14404k reserved, 916k data, 364k init, 0k highmem)
[   43.033155] virtual kernel memory layout:
[   43.033160]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   43.033167]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   43.033174]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   43.033180]     lowmem  : 0xc0000000 - 0xd8000000   ( 384 MB)
[   43.033186]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   43.033193]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   43.033199]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   43.033214] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   43.033364] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   43.113389] Calibrating delay using timer specific routine.. 898.68 BogoMIPS (lpj=1797375)
[   43.113498] Security Framework v1.0.0 initialized
[   43.113529] SELinux:  Disabled at boot.
[   43.113598] Mount-cache hash table entries: 512
[   43.114099] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   43.114146] CPU: L1 I cache: 16K, L1 D cache: 16K
[   43.114158] CPU: L2 cache: 512K
[   43.114170] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   43.114215] Compat vDSO mapped to ffffe000.
[   43.114266] Checking 'hlt' instruction... OK.
[   43.129741] SMP alternatives: switching to UP code
[   43.130375] Freeing SMP alternatives: 11k freed
[   43.131450] Early unpacking initramfs... done
[   44.567279] CPU0: Intel Pentium III (Katmai) stepping 02
[   44.567304] SMP motherboard not detected.
[   44.567314] Local APIC not detected. Using dummy APIC emulation.
[   44.567497] Brought up 1 CPUs
[   44.567995] Booting paravirtualized kernel on bare hardware
[   44.568170] Time: 15:17:42  Date: 01/01/108
[   44.568276] NET: Registered protocol family 16
[   44.568667] EISA bus registered
[   44.569487] PCI: PCI BIOS revision 2.10 entry at 0xfd983, last bus=1
[   44.569499] PCI: Using configuration type 1
[   44.569509] Setting up standard PCI resources
[   44.575734] ACPI: Interpreter disabled.
[   44.575752] Linux Plug and Play Support v0.97 (c) Adam Belay
[   44.575790] pnp: PnP ACPI: disabled
[   44.575805] PnPBIOS: Scanning system for PnP BIOS support...
[   44.575858] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
[   44.575873] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e31, dseg 0x400
[   44.583834] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   44.584075] PCI: Probing PCI hardware
[   44.584109] PCI: Probing PCI hardware (bus 00)
[   44.584647] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   44.584656] * this clock source is slow. Consider trying other clock sources
[   44.584725] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   44.584739] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   44.587987] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   44.590402] NET: Registered protocol family 8
[   44.590414] NET: Registered protocol family 20
[   44.590717] pnp: 00:00: ioport range 0x370-0x371 has been reserved
[   44.590738] pnp: 00:00: iomem range 0xfffc0000-0xffffffff could not be reserved
[   44.590767] pnp: 00:01: iomem range 0x0-0x9ffff could not be reserved
[   44.590781] pnp: 00:01: iomem range 0xe4000-0xfffff could not be reserved
[   44.590796] pnp: 00:01: iomem range 0x100000-0x17ffffff could not be reserved
[   44.590811] pnp: 00:01: iomem range 0xfff80000-0xfffbffff has been reserved
[   44.590848] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   44.590863] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[   44.590877] pnp: 00:0a: ioport range 0x7000-0x700f has been reserved
[   44.590902] pnp: 00:0c: iomem range 0xc9800-0xcbfff has been reserved
[   44.592673] PCI: Failed to allocate mem resource #6:10000@fd000000 for 0000:01:00.0
[   44.592741] PCI: Bridge: 0000:00:01.0
[   44.592749]   IO window: disabled.
[   44.592764]   MEM window: f5000000-f5ffffff
[   44.592777]   PREFETCH window: fc000000-fcffffff
[   44.592838] NET: Registered protocol family 2
[   44.593064] Time: tsc clocksource has been installed.
[   44.625268] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   44.625478] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   44.626296] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   44.626854] TCP: Hash tables configured (established 16384 bind 16384)
[   44.626866] TCP reno registered
[   44.637591] checking if image is initramfs... it is
[   47.408756] Freeing initrd memory: 7053k freed
[   47.410015] audit: initializing netlink socket (disabled)
[   47.410064] audit(1201879064.064:1): initialized
[   47.422064] VFS: Disk quotas dquot_6.5.1
[   47.422368] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   47.423101] io scheduler noop registered
[   47.423114] io scheduler anticipatory registered
[   47.423124] io scheduler deadline registered
[   47.423236] io scheduler cfq registered (default)
[   47.423272] Limiting direct PCI/PCI transfers.
[   47.423334] Boot video device is 0000:01:00.0
[   47.423933] isapnp: Scanning for PnP cards...
[   47.778379] isapnp: No Plug & Play device found
[   47.939680] Real Time Clock Driver v1.12ac
[   47.940043] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   47.940241] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   47.943366] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   47.947286] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   47.947974] input: Macintosh mouse button emulation as /class/input/input0
[   47.948511] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   47.951129] serio: i8042 KBD port at 0x60,0x64 irq 1
[   47.951152] serio: i8042 AUX port at 0x60,0x64 irq 12
[   47.952052] mice: PS/2 mouse device common for all mice
[   47.952771] EISA: Probing bus 0 at eisa.0
[   47.952803] Cannot allocate resource for EISA slot 1
[   47.952853] Cannot allocate resource for EISA slot 7
[   47.952864] Cannot allocate resource for EISA slot 8
[   47.952873] EISA: Detected 0 cards.
[   47.953317] TCP cubic registered
[   47.953390] NET: Registered protocol family 1
[   47.953497] Using IPI No-Shortcut mode
[   47.953843]   Magic number: 12:358:284
[   47.953916]   hash matches device ttyvf
[   47.955633] Freeing unused kernel memory: 364k freed
[   48.016475] input: AT Translated Set 2 keyboard as /class/input/input1
[   49.945880] AppArmor: AppArmor initialized<5>audit(1201879066.564:2):  type=1505 info="AppArmor initialized" pid=1117
[   49.979161] fuse init (API version 7.8)
[   50.004137] Failure registering capabilities with primary security module.
[   50.088106] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   52.340227] usbcore: registered new interface driver usbfs
[   52.340334] usbcore: registered new interface driver hub
[   52.340461] usbcore: registered new device driver usb
[   52.347723] USB Universal Host Controller Interface driver v3.0
[   52.347944] PCI: setting IRQ 9 as level-triggered
[   52.347958] PCI: Found IRQ 9 for device 0000:00:07.2
[   52.347992] PCI: Sharing IRQ 9 with 0000:00:10.0
[   52.348023] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   52.348400] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   52.348458] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[   52.349015] usb usb1: configuration #1 chosen from 1 choice
[   52.349147] hub 1-0:1.0: USB hub found
[   52.349185] hub 1-0:1.0: 2 ports detected
[   52.552594] SCSI subsystem initialized
[   52.608607] libata version 2.21 loaded.
[   52.642775] ata_piix 0000:00:07.1: version 2.11
[   52.643405] scsi0 : ata_piix
[   52.643629] scsi1 : ata_piix
[   52.643751] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011000 irq 14
[   52.643769] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011008 irq 15
[   52.643828] ata1: port disabled. ignoring.
[   52.753030] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   52.753567] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   52.753584] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   52.932708] usb 1-1: configuration #1 chosen from 1 choice
[   52.960613] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   53.175226] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   53.338525] usb 1-2: configuration #1 chosen from 1 choice
[   53.342346] hub 1-2:1.0: USB hub found
[   53.345201] hub 1-2:1.0: 4 ports detected
[   53.375351] ata2.00: ATAPI: Hewlett-Packard CD-Writer Plus 9100, 1.0c, max UDMA/33
[   53.375385] ata2.01: ATAPI: LS-120 F200   08              UHD Floppy, 0220K009, max PIO2
[   53.547349] ata2.00: configured for UDMA/33
[   53.661070] usb 1-2.3: new full speed USB device using uhci_hcd and address 4
[   53.719354] ata2.01: configured for PIO2
[   53.724365] scsi 1:0:0:0: CD-ROM            HP       CD-Writer+ 9100  1.0c PQ: 0 ANSI: 5
[   53.728582] scsi 1:0:1:0: Direct-Access     MITBISHI LS-120 F200   08 0220 PQ: 0 ANSI: 5
[   53.729164] PDC20262: IDE controller at PCI slot 0000:00:0f.0
[   53.729194] PCI: setting IRQ 10 as level-triggered
[   53.729206] PCI: Found IRQ 10 for device 0000:00:0f.0
[   53.729257] PDC20262: chipset revision 1
[   53.729271] PDC20262: ROM enabled at 0x20000000
[   53.729281] PDC20262: 100% native mode on irq 10
[   53.729303] PDC20262: (U)DMA Burst Bit ENABLED Primary PCI Mode Secondary PCI Mode.
[   53.729317]     ide2: BM-DMA at 0x1080-0x1087, BIOS settings: hde:pio, hdf:pio
[   53.729358]     ide3: BM-DMA at 0x1088-0x108f, BIOS settings: hdg:pio, hdh:pio
[   53.729391] Probing IDE interface ide2...
[   53.835385] usb 1-2.3: configuration #1 chosen from 1 choice
[   53.963221] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   53.963241] Uniform CD-ROM driver Revision: 3.20
[   53.964196] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   54.017045] hde: MAXTOR STM3160812A, ATA DISK drive
[   54.019965] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   54.020661] sd 1:0:1:0: Attached scsi generic sg1 type 0
[   54.030008] sd 1:0:1:0: [sda] Attached SCSI removable disk
[   54.295058] hdf: WDC AC313500D, ATA DISK drive
[   54.351110] hde: selected mode 0x44
[   54.351585] hdf: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   54.351597] hdf: selected mode 0x42
[   54.351913] ide2 at 0x10c0-0x10c7,0x1016 on irq 10
[   54.352188] Probing IDE interface ide3...
[   54.919211] 8139cp 0000:00:10.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   54.919231] 8139cp 0000:00:10.0: Try the "8139too" driver instead.
[   54.936494] 8139too Fast Ethernet driver 0.9.28
[   54.937898] PCI: Enabling device 0000:00:10.0 (0104 -> 0107)
[   54.937924] PCI: Found IRQ 9 for device 0000:00:10.0
[   54.937948] PCI: Sharing IRQ 9 with 0000:00:07.2
[   54.939236] eth0: RealTek RTL8139 at 0xd880e000, 00:14:6c:8e:7a:ed, IRQ 9
[   54.939250] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   54.969493] hde: max request size: 512KiB
[   55.011912] hde: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(66)
[   55.036323] hde: cache flushes supported
[   55.036469]  hde: hde1 hde2 < hde5 >
[   55.085643] hdf: max request size: 128KiB
[   55.096070] hdf: 26520480 sectors (13578 MB) w/1966KiB Cache, CHS=26310/16/63, UDMA(33)
[   55.096093] hdf: cache flushes not supported
[   55.096201]  hdf: hdf1
[   55.840757] Attempting manual resume
[   55.840774] swsusp: Resume From Partition 33:5
[   55.840782] PM: Checking swsusp image.
[   55.841055] PM: Resume from disk failed.
[   55.971529] EXT3-fs: INFO: recovery required on readonly filesystem.
[   55.971548] EXT3-fs: write access will be enabled during recovery.
[   57.855387] kjournald starting.  Commit interval 5 seconds
[   57.855438] EXT3-fs: recovery complete.
[   57.867417] EXT3-fs: mounted filesystem with ordered data mode.
[   73.958958] Linux agpgart interface v0.102 (c) Dave Jones
[   73.976391] agpgart: Detected an Intel 440BX Chipset.
[   73.983403] agpgart: AGP aperture is 64M @ 0xf8000000
[   74.002761] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   74.012989] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   74.503686] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   74.517123] input: PC Speaker as /class/input/input2
[   75.118792] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   75.768613] parport_pc 00:14: reported by Plug and Play BIOS
[   75.768696] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   78.250949] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: Disabling reads from problem bidirectional printer on usblp0
[   78.257334] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Unidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0104
[   78.257406] usbcore: registered new interface driver usblp
[   78.257422] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   78.565054] PCI: Enabling device 0000:00:0c.0 (0104 -> 0105)
[   78.565081] PCI: setting IRQ 11 as level-triggered
[   78.565092] PCI: Found IRQ 11 for device 0000:00:0c.0
[   78.565122] PCI: Sharing IRQ 11 with 0000:00:0e.0
[   78.565139] PCI: Sharing IRQ 11 with 0000:01:00.0
[   80.332824] lp0: using parport0 (interrupt-driven).
[   80.469654] Adding 1124508k swap on /dev/hde5.  Priority:-1 extents:1 across:1124508k
[   80.973600] EXT3 FS on hde1, internal journal
[   84.377847] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   84.378261] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   84.379466] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   84.380025] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   87.376133] ppdev: user-space parallel port driver
[   88.003385] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   88.609786] audit(1201897106.594:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4357 profile="/usr/sbin/cupsd"
[   88.917831] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   90.453153] Failure registering capabilities with primary security module.
[   92.125746] Bluetooth: Core ver 2.11
[   92.126188] NET: Registered protocol family 31
[   92.126202] Bluetooth: HCI device and connection manager initialized
[   92.126217] Bluetooth: HCI socket layer initialized
[   92.228106] Bluetooth: L2CAP ver 2.8
[   92.228125] Bluetooth: L2CAP socket layer initialized
[   92.281075] Bluetooth: RFCOMM socket layer initialized
[   92.281494] Bluetooth: RFCOMM TTY layer initialized
[   92.281508] Bluetooth: RFCOMM ver 1.8
[   96.150572] NET: Registered protocol family 17
[   98.667798] NET: Registered protocol family 10
[   98.668230] lo: Disabled Privacy Extensions
[  109.542693] eth0: no IPv6 routers present
[  431.946175] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  431.946204] hde: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  431.946220] ide: failed opcode was: unknown
[  434.561899] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[  434.561929] hde: dma_intr: error=0x84 { DriveStatusError BadCRC }
[  434.561945] ide: failed opcode was: unknown
bill@OldGateway:~$

---

### Post by billnj on 2008-02-04
Still no sound and not a clue as to how I can get it.  According to the alsa website and Ubuntu info, my ens1371 driver is compatible.  No matter what I do I can't get sound to work.

I have manually loaded the driver, automatically loaded the driver as it says to in the Ubuntu comprehensive sound guide, and followed numerous threads trying nearly everything to get sound.

I am completely out of ideas.  Can anyone help a new user?  I've hit a major dead end.

:confused:

---

