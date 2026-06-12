---
title: "[SOLVED] Sound has disappeared"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2007-09-22
I've been using Feisty now for several months, and my sound has never been an issue.  Then, suddenly today, it's gone.  I did no updates in the past couple days, changed nothing at all.

I have an Intel ICH sound card.  **** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I was on the net, playing some games, which I have played before (nothing out of the ordinary).  I downloaded nothing, didn't change my volume as far as I can remember.  I left the computer on, when to have some dinner, came back and there is no sound.  Like, it just disappeared.  Noone else touched the computer either.

I looked at several posts but "MY" answer didn't seem to be in there.  I checked the Alsa mixer, and it's looking same as usual.  Really, I did nothing.  I wonder if my sound card died, or something.

Is it possible the sound is muted, out there?  Someplace elusive?

(PS  I don't know much about this sort of thing, so if you need any real specific info about the sound card, etc. please tell me how to get that info to you - thanks.)

---

### Post by moeFinley on 2007-09-22
does this give you any sound?```
aplay -vv /usr/share/firefox/res/samples/test.wav
```

---

### Post by Motorhead Kaze on 2007-09-22
Hello.  No, that didn't do anything.  I saw the little bar move across the terminal window (indicating some sound was being played) but heard nothing.  Thanks anyway.

---

### Post by moeFinley on 2007-09-22
That really suggests something physical, broken speakers etc.  Do you have two sound cards in the machine and it's now outputting to the other?  Or maybe just more than one output on the same card ie. digital and analog.

---

### Post by Motorhead Kaze on 2007-09-22
"As far as I know"  There's just the one sound card.  The "ICH" one.  

When looking at Sound Preferences, I see a Realtek ALC655 rev 0 (OSS mixer) listed under my Intel ICH (Alsa mixer).

If you need me to check anything else, I'd be happy to.  

Thanks this far anyhow.

---

### Post by Linux_Man on 2007-09-22
Did you restart? Because sometimes the sound messes up and I restart it and it helps. If not then try restarting the sound daemon.

---

### Post by Motorhead Kaze on 2007-09-22
Ah yes.  I first tried just a simple CTL ALT BKSP, that didn't work so I restarted the computer.  Since that didn't work, I shut down, and left it off for 5 or more minutes, came back, still no sound.

How might I restart the Daemon?  (I don't know what that is, sorry)

---

### Post by Pumalite on 2007-09-22
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by Linux_Man on 2007-09-22
A Daemon is equivilent to a process in windows. But go to your system monitor and restart the process esd, the gnome sound daemon, that should fix it unless your using KDE apps that I can't think of it's sound daemon.

---

### Post by Motorhead Kaze on 2007-09-22
>Pumalite   I'm still reading through the page you gave me.  Thanks.  Trying some things in there, so far not much happening, but I'm working on it.

> Linux Man, I did open the System Monitor and the ESD process is sleeping.  Right clicking only gives me options to Stop, Continue, End or Kill Process, but unfortunately there is no option for restarting it.  Another way perhaps?

BTW, is the "Mixer Applet" relevant here?  It's sleeping too.

---

### Post by Pumalite on 2007-09-22
That page I gave you is the key to your problem. Read it carefully.

---

### Post by Motorhead Kaze on 2007-09-22
OK.  I have tried all the rebooting/updating/checking things mentioned on the Ubuntu Sound links posted  (Meaning I read the pages and followed the instructions as written) I rebooted and there is still no sound.

Anyone know how to check if the physical sound card is dead?  I mean really, I had sound 3 hours ago, I did nothing at all strange or touching any volume controls or downloading anything, and the sound was just gone.

---

### Post by Pumalite on 2007-09-22
Post:

sudo lshw

---

### Post by Motorhead Kaze on 2007-09-22
description: Motherboard
       product: C51MCP51
       physical id: 0
       slot: FDD
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/22/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.2
          slot: Socket 940
          size: 1800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51G [GeForce 6100]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          size: 256MB
          width: 64 bits
          clock: 66MHz
          capabilities: vga bus_master cap_list
          configuration: driver=nvidia latency=0
          resources: iomemory:fb000000-fbffffff iomemory:d0000000-dfffffff iomemory:fc000000-fcffffff irq:20
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: ioport:1c00-1c3f ioport:1c40-1c7f irq:10
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@00:0a.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fe02f000-fe02ffff irq:16
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.20-16-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=8 speed=12.0MB/s
           *-usb:0
                description: Mouse
                product: ET-0405A-UV2.0-1
                vendor: WACOM
                physical id: 3
                bus info: usb@1:3
                version: 2.01
                capabilities: usb-1.01
                configuration: driver=wacom maxpower=40mA speed=1.5MB/s
           *-usb:1
                description: USB hub
                product: Standard USB Hub
                physical id: 5
                bus info: usb@1:5
                version: 3.00
                capabilities: usb-1.10
                configuration: driver=hub maxpower=64mA slots=4 speed=12.0MB/s
           *-usb:2
                description: Printer
                product: deskjet 3420
                vendor: hp
                physical id: 6
                bus info: usb@1:6
                version: 1.00
                serial: TH2AQ3C1Y141
                capabilities: usb-2.00 bidirectional
                configuration: driver=usblp maxpower=2mA speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fe02e000-fe02e0ff irq:17
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.20-16-generic ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
           *-usb
                description: Mass storage device
                product: I-O DATA iU-HD
                vendor: I-O DATA DEVICE,INC
                physical id: 4
                bus info: usb@2:4
                logical name: scsi2
                version: 11.00
                serial: 0B000116068DBFAD
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=98mA speed=480.0MB/s
              *-disk
                   description: SCSI Disk
                   product: R120L0
                   vendor: Maxtor 4
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sda
                   version: RAMB
                   size: 114GB
                   capabilities: partitioned partitioned:dos
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      logical name: /dev/sda1
                      capacity: 114GB
                      capabilities: primary
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:f400-f40f
        *-ide:0
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-disk
                description: ATA Disk
                product: ST3320620A
                vendor: Seagate
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                version: 3.AAE
                serial: 9QF4HNBB
                size: 298GB
                capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                configuration: mode=udma5 smart=on
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: ide@0.0,1
                   logical name: /dev/hda1
                   capacity: 295GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: ide@0.0,2
                   logical name: /dev/hda2
                   size: 2588MB
                   capacity: 2588MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/hda5
                      capacity: 2588MB
                      capabilities: nofs
        *-ide:1
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom
                description: DVD-RAM writer
                product: DVD DC DW1670
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: 100
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: mode=udma4
              *-disc
                   physical id: 0
                   logical name: /dev/hdc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9f0-9f7 ioport:bf0-bf3 ioport:970-977 ioport:b70-b73 ioport:e000-e00f iomemory:fe02d000-fe02dfff irq:18
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Multimedia audio controller
          product: MCP51 AC97 Audio Controller
          vendor: nVidia Corporation
          physical id: 10.2
          bus info: pci@00:10.2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: ioport:dc00-dcff ioport:d800-d8ff iomemory:fe02c000-fe02cfff irq:16
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@00:14.0
          logical name: eth0
          version: a1
          serial: 00:e0:4c:ed:05:76
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full ip=220.36.24.62 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: iomemory:fe02b000-fe02bfff ioport:d400-d407 irq:19
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by Motorhead Kaze on 2007-09-22
Good morning.  Is that what you wanted me to post?

---

### Post by Pumalite on 2007-09-22
I didn't see your sound controller. Maybe I'm not familiar with your motherboard and you could point it to me?

---

### Post by Motorhead Kaze on 2007-09-23
Ah, sorry I was off the PC for a bit.  Thanks for your continued help.

Turning on the computer this morning, I clicked the volume icon, and got a message saying,

“The volume control did not find any elements and or devices to control.  This means either that you don't have the right Gstreamer plugins installed, or that you don't have a sound card configured.”

Clicking on the volume icon again, I get a "No volume control Gstreamer plugins or devices found" message when clicking on the volume control icon.  

I tried reinstalling all the GStreamer related bits in Synaptic, and nothing happened.  So... do sound cards just break?  A workmate built this PC and I would imagine, that many parts, including the sound card were very likely used when he put it in here.  (My HD totally burned and died just after 10 months of using this "New" computer)

If you still think there's a chance it's useful, how would I point you to my motherboard?  Sorry, I spent the last bunch of years just clicking "Yes" to little windows.  And, as it turns out, I know far less about computers than I thought, so if you wouldn't mind, telling me how to show you my motherboard, I'll do it.

Thanks again for your help.

---

### Post by Pumalite on 2007-09-23
The kernel loads the modules according to the hardware that it detects. Apparently is not detecting yours. I bet you have a long booting time. Go to System>Preferences>Sound and configure your card.

---

### Post by Motorhead Kaze on 2007-09-23
Well, booting time has increased yes.  I was assuming it was from downloading more and more programs to do this and that.

In Sound Preferences, Devices, the choices are Sound Events, Music and Movies, Audio Conferencing and Default Mixer Tracks.  The top 3 are set to Autodetect, and today, there are NO Default mixer tracks to choose from, whereas yesterday there were the Alsa and OSS.

---

### Post by Pumalite on 2007-09-23
If I were you I would get a good Sound Blaster and stick it in there.

---

### Post by Motorhead Kaze on 2007-09-23
Since looking does no harm, I opened up the case to just look at the "Sound card" and it is nothing but a little silver cube.  Am I right in guessing that it is actually not a sound "Card" but actually FIXED to the motherboard?  If it isn't removable, then I will need a whole new motherboard yes?

Soundblaster sounds ... powerful, but is it something I can just buy and plug in somewhere?

Thanks for all your help and the time.  Really.

---

### Post by moeFinley on 2007-09-24
You don't need to buy a new motherboard.  The built-in sound card on the motherboard can be disabled in the bios.  Then you can add a new sound card to any spare[ PCI slot]("http://en.wikipedia.org/wiki/Image:Pci-slots.jpg").

It maybe the case that somehow your sound card has simple been disabled in the bios and you just need to re-enable it.

Soundblaster is a brand of sound cards.  The chip on your current motherboard is a Soundblaster so another one would be a good replacement.  But you may just want to buy the cheapest you can find just as a test.  Soundcards start from about £5 in the UK and I'm sure there even cheaper in Japan.

---

### Post by Motorhead Kaze on 2007-09-24
Thanks Moe.  Funny, even though I haven't fixed the problem yet, all the help makes me feel good. (Not warm and fuzzy mind you, just good).  Haha.  Tomorrow morning I'll open up the beast and look at the PCI slots.  For now, I'll get on the forums and look for how to get into BIOS and check if my soundcard is disabled.  One of the other fellas mentioned that as well, at the time I misunderstood Bios as meaning Synaptic, not "BIOS".  Not a place I generally visit.

...feels like I'm going to see the architect or the oracle or something...

Thanks!

---

### Post by Hero of Time on 2007-09-24
You can get into the BIOS by rebooting and press the key that is noted there to enter Setup. Usually it's DEL, F2 or F10.

I'm having a similar problem. After I had a few other problems with my profile and time, I wanted to check if my settings from my media players were saved. Opening Audicious, I got the message "couldn't open audio". Using 'lspci' I can see my soundcard, but in options it doesn't show. With the mixer same thing. Only thing I did was update to the latest Linux Headers (for the 4th time the same version, probably build number is different, which isn't shown by default).

I will add extra device info shortly
Extra info:

lshw:
```
    description: Notebook
    product: AMILO PI 1536
    vendor: FUJITSU SIEMENS
    version: Not Applicable
    serial: 531171D1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=00D0E151-CD63-0010-9302-C8913D38C486
  *-core
       description: Motherboard
       product: AMILO PI 1536
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
       slot: PEG Slot J6C1
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS
          physical id: 0
          version: 1.15 (08/03/2006)
          size: 1MB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 1GHz
          capacity: 2048MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GB
          capacity: 3GB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 512MB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: Radeon Mobility X1400
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        [b]*-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel[/b]
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth1
                version: 02
                serial: 00:13:02:15:07:50
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.252 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=3 module=ohci1394
           *-network
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:05:05.0
                logical name: eth0
                version: 10
                serial: 00:03:0d:44:7f:69
                size: 1GB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.1 latency=32 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=1GB/s
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: DVD+-RW SDVD8820
                vendor: PHILIPS
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AJ10
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: SCSI Disk
                product: FUJITSU MHV2100B
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: NW77T66279HC
                size: 93GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 10GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 7687MB
                   capabilities: primary
              *-volume:2
                   description: HPFS/NTFS partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 74GB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 1145MB
                   capacity: 1145MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1145MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```
Bold piece is my sound card, makes sence doesn't it :P.

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

I know for sure that the card isn't malfunctioning, as it works just fine in XP. I know I run Gutsy and therefor bound to have problems sooner or later, but I doubt the programmers would make a mistake like this. Just to be sure, I booted to an earlier version of the headers (or kernel, whatever) and it has the same problem. My Sound Mixer is empty, no useful controls selectable.

In case anyone needs to know, I run Xubuntu (Xfce).

Ok, new development. It's in my profile. I have no idea where the settings are stored about audio, but when I play stuff as root, everything works just fine. It seems that I'm not allowed to open the audio controller. Anyone know how to add myself to the config file so I can play music again? I already tried removing my profile using 'userdel' and removing my home folder (/home/username) and then create my user again using 'adduser', but that didn't work.

---

### Post by Hero of Time on 2007-09-26
Bump. Anyone as any idea as what my problem might be and how to solve it?

Never mind, got it fixed. I added myself to the audio group via /etc/group.

---

### Post by Motorhead Kaze on 2007-10-02
Hero of time! (And others who were helping)  Sorry, I was gone a bit.  Trying to decide if I'd buy a sound card...then I got some brains and booted Ubuntu of the disc and there my sound is.  I'm going to play with H.O.T.'s (neat acronym) idea there.

How did you add yourself on the profile you mentioned last? I opened "Group" under the etc file and really have no clue what I'm looking at.  I see my user name (kaze) all over the place in there, so where is it that I should be adding?  ....shite English, oh well.

---

### Post by CalvinK on 2007-10-02
> **Hero of Time said:**
> Bump. Anyone as any idea as what my problem might be and how to solve it?

Never mind, got it fixed. I added myself to the audio group via /etc/group.

I had the same problem after the new update which broke alsa. Just reinstall (recompile) alsa-driver, utils and lib and it should work or do it with synaptic.

---

### Post by JackDog on 2007-10-02
I also have experienced this. It worked with gutsy a couple weeks back but in the last week it has not. The module that I used to load for the sound card is no longer present (snd-hda-intel).

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

Currently I cannot find the kernel module anywhere.

---

### Post by Pumalite on 2007-10-02
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Motorhead Kaze on 2007-10-02
Okay, so I am perhaps "A wuss" (haha) but, really, for days and days I've just been reading so many posts on sound issues I had had it.  It seems like there is a sound problem for every type of computer and person.  I tried the things I was offered, and just either didn't "Do it right" or it didn't work for my computer.  I'm guessing I missed a step somewhere, but honestly, it's not really as simple as "Copy and paste" into the command line, there is a lot of research and question asking involved.  Time just isn't something I have right now.

I just said, "Screw it" and put the Ubuntu disc in and booted off the disc.  The sound worked fine.  So how about THAT! ?

Just out of quasi-geek curiosity, I decided to put in XP to see if perhaps it would find the sound.  And it didn't.   Using XP after months of not using it, was a bit like calling an ex-girlfriend...feelin' like I need closure now.  (Ew.)  So then I loaded the 'Buntu disc and....sound was fine. 

I attempted to put Ubuntu back WITH XP and got some gnarley screen with warnings about my messed up /etc/x11/xorg.conf  and I got started in with questions I had NO way to answer.  Like I know my mouse protocol and my x server driver's NAME.  So fine, I just reinstalled 'Buntu without any ol' XP.  Did the 'Guided install using whole disc' and now, everything is back to normal, with sound, with my Nvidia driver all happy.  Of course, I'll have to reinstall....everything, but at least there is sound and all the pieces are running correctly.

Anyway, blathering aside, **how is it possible that the sound card wasn't recognized by either OS, yet when run off the disc, the sound worked great?**  That isn't "Logical" to me, so if someone could 'splain it, I would be super happy.

Thanks for all your guys' help.  Sorry I had to do it the "Hard way" an reinstall but I had to do it.

(Message to Pumalite, you are a helpful person.  All over these posts!  I notice you use Lautrec's image on your posts.   Just in case you were interested, yesterday I went to a Lautrec show here in Osaka, and saw 3 versions of that poster, live.  BIG is a good word.  The man in the poster was apparently an actor famous for just coming on stage and insulting the audience.  He referred to his audience as "Pigs".  Just a little side bit for you.)

Thanks guys.  Over and out until the next problem.

---

### Post by Pumalite on 2007-10-02
You have to admit that is one of Henri's better posters. And he painted it while hanging out at a Monmartre's dives, drunk as usual.

---

### Post by dbott67 on 2007-10-02
From some previous threads I've posted in:

After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.
[COLOR=Blue][U][B]
My suggestion is this:[/B][/U][/COLOR]

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

-Dave

---

### Post by Motorhead Kaze on 2007-10-03
See, now it's the simple things like "Creating a new account to see if that works" that really made Bart Simpson's father's "Doh!" so popular.

Dang.  

Thanks for that.  I'll make the note!  (Sheeesh.)

---

### Post by cherry316316 on 2007-10-08
> **Motorhead Kaze said:**
> See, now it's the simple things like "Creating a new account to see if that works" that really made Bart Simpson's father's "Doh!" so popular.

Dang.  

Thanks for that.  I'll make the note!  (Sheeesh.)

[http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)

---

### Post by Asger on 2007-10-22
Hi there,

I had more or less the same problem. I went into alsamixer and turned everything on which apparently did not work but after stopping and continuing the esd process I have sound again. Thanks for all the good forum posts.

Asger

---

