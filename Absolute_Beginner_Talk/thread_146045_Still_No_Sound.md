---
title: "Still No Sound"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by cryptidan on 2006-03-17
But finding all kinds of different ways for the system to tell me that it ain't gonna work...How exciting. Now whats all this?

(on next page, apparently I can't put it all here...)

edit: nevermind, I just missed the code thing at first, but nonetheless, still took two replies...

---

### Post by cryptidan on 2006-03-17
```
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
snd_pcm_open: No such file or directory (default)
Failed to initialize plugin!
Failed to register plugin: /usr/lib/alsaplayer/output/libalsa_out.so
Failed to load output plugin "alsa". Trying defaults.
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
snd_pcm_open: No such file or directory (default)
Failed to initialize plugin!
/usr/lib/alsaplayer/output/libalsa_out.so failed to load
error opening /dev/dsp
Failed to initialize plugin!
/usr/lib/alsaplayer/output/liboss_out.so failed to load
NOTE: THIS IS THE NULL PLUGIN.      YOU WILL NOT HEAR SOUND!!
Session "alsaplayer-0" is ready.
```

---

### Post by Swab on 2006-03-17
What are you trying to do, and where are you seeing these messages?  Are you using an account that is a member of the audio group?

---

### Post by cryptidan on 2006-03-17
I apologize for not explaining, a little frustrated, (this is day 3 of no sound)

1. Volume control:The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

XMMS:couldn't open audio
          please check that your soundcard is configured properly
          you have the correct output plugin selected
          no other program is blocking the soundcard

Multimedia System Selector: Failed to construct test pipeline for 'OSS - Open Sound System
and ALSA, and ESD, etc...

I've looked everywhere, to no avail...

---

### Post by mlind on 2006-03-17
could you post the contens of /proc/asound/cards

---

### Post by cryptidan on 2006-03-17
contents of /proc/asound/cards:

--- no soundcards ---


D'oh!  But I do have one...I think...can I fix this?

Looked in there, says its an ESS Audiodriver  (this comp is a little dated, I know, I'm cheap, I buy refurbished stuff)

---

### Post by mlind on 2006-03-17
ALSA modules are not loaded then. What's you're sound card?
Do you have multiple soundcards?

use *sudo lshw* to display it

---

### Post by cryptidan on 2006-03-17
Ah, here ya go, I can't figure out if its in there or not....

```
 description: Mini Tower Computer
    product: Deskpro
    vendor: Compaq
    serial: 6020DKZ2B548
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
    configuration: boot=normal chassis=mini-tower uuid=B2667E38-51E1-D411-8AE6-98C36CAB28EB
  *-core
       description: Motherboard
       product: 0400h
       vendor: Compaq
       physical id: 0
       serial: 6020DKZ2B548
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 686T3 (08/18/99)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: J22
          size: 650MHz
          capacity: 950MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: burst internal write-through
        *-cache:1
             description: L2 cache
             physical id: a
             slot: Cache L2
             size: 256KB
             capacity: 4MB
             capabilities: burst internal write-through
     *-memory:0
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          capacity: 384MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM #1: J10
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM #2: J11
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM #3: J12
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 22
          slot: System board or motherboard
          capacity: 256KB
        *-bank UNCLAIMED
             description: Chip FLASH
             physical id: 0
             slot: AM29F002: U35
             size: 256KB
             width: 16 bits
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 44000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:44000000-47ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 3D Rage Pro AGP 1X/2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 5c
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:40000000-40ffffff ioport:1000-10ff iomemory:41000000-41000fff irq:11
        *-network
             description: Ethernet interface
             product: 3c905B 100BaseTX [Cyclone]
             vendor: 3Com Corporation
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 64
             serial: 00:50:da:b1:6e:47
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.0.102 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:2000-207f iomemory:41100000-4110007f irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@00:14.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@00:14.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:20a0-20af
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: Maxtor 91024U3
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: RA530JN0
                   serial: H3H1X01C
                   size: 9541MB
                   capacity: 9541MB
                   capabilities: ata dma lba iordy smart pm apm
                   configuration: apm=off mode=udma2 smart=on
              *-disk:1
                   description: ATA Disk
                   product: WDC WD400BB-00DEA0
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 05.03E05
                   serial: WD-WMAD15143964
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: mode=udma2 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: IDE CD-ROM
                   product: Compaq CRD-8402B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.01
                   serial: 2000/02/01
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
              *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: LITE-ON LTR-48246S
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: SS09
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@00:14.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:2080-209f irq:11
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: NOMAD Jukebox 2
                   vendor: Creative Technology
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.01
                   serial: 64FF09F17CD10F12
                   capabilities: usb-2.00
                   configuration: maxpower=0mA speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@00:14.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9

```

---

### Post by mlind on 2006-03-17
[QUOTE=cryptidan]Ah, here ya go, I can't figure out if its in there or not....[/QUOTE]

Me neither.. I've got separate multimedia section on the lswh listing, but yours
doesn't have one. Is it integrated soundchip?

---

### Post by cryptidan on 2006-03-17
Yes, it is, Like I said before there is on chip in there that reads Ess audiodriver, so...

also, let me mention that a few of the errors told me there is another application using the soundchip, adn it also mentioned artsd, but when i disabled artsd it still gave me the errors, maybe faulty?  I mean, I just bought this tower Tuesday!

---

### Post by mlind on 2006-03-17
[QUOTE=cryptidan]Yes, it is, Like I said before there is on chip in there that reads Ess audiodriver, so...

also, let me mention that a few of the errors told me there is another application using the soundchip, adn it also mentioned artsd, but when i disabled artsd it still gave me the errors, maybe faulty?  I mean, I just bought this tower Tuesday![/QUOTE]


does "Compaq ESS 1869 5-watt audio Board" ring any bells?
if it does then [this]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx") ALSA page could help.

Could you also provide output of *lsmod | grep snd*

---

### Post by cryptidan on 2006-03-17
> does "Compaq ESS 1869 5-watt audio Board" ring any bells?
if it does then this ALSA page could help.

Could you also provide output of lsmod | grep snd

```
frankenstein@oldmine:~$ lsmod | grep snd
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  1 snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  5 snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  1 snd
```

Oh! if i used Automatix, wouldn't this mean alsa is there?

---

### Post by cryptidan on 2006-03-18
I'm back, oh yes, and going on day 4 of no sound/no idea of what the problem is....

---

### Post by arnieboy on 2006-03-18
try using the "**gnome sound fix**" option in the **latest version** of Automatix (**5.6.2**). However, one caveat: when logging into Gnome from GDM (use the "Gnome" option, not the "Default" option even if its set to Gnome)

---

### Post by cryptidan on 2006-03-18
Went thru Automatix yesterday...

Here's what it says now:

Error playing CD.

Reason: Device "/dev/dsp" does not exist.

---

### Post by therunnyman on 2006-03-18
Hi Cryptidian,

This'll probably add to your frustration, but I wonder, could you give me a joe six-pack walkthrough of what happened?  I mean something like:

My machine has an onboard sound device.  I installed Ubuntu on said machine.  I tried to play an .mp3 or a CD, and no sound came out.  Then I did X and that didn't work.  Then I did Y and that didn't work.

I think we can fix this really fast, but I'm having difficulty gleaning exactly what happened from the other posts.

therunnyman

---

### Post by cryptidan on 2006-03-18
> This'll probably add to your frustration, but I wonder, could you give me a joe six-pack walkthrough of what happened? I mean something like:

My machine has an onboard sound device. I installed Ubuntu on said machine. I tried to play an .mp3 or a CD, and no sound came out. Then I did X and that didn't work. Then I did Y and that didn't work.

I think we can fix this really fast, but I'm having difficulty gleaning exactly what happened from the other posts.

You basically said it all, what all was posted on this thread...Up until "then I did X"

Here's what I did, I came to the extremely confusing forum here, and spent a total of 12 hours straight looking over everything that had to do with sound, audio, cards, applications, whatever, to no avail whatsoever, so no, I am not going to spend an extra hour here typing in every remedy that was posted on this forum that I tried, you can look em up.  **If its posted on this board, I tried it.**

But let me go over again what I have gleaned fom this experience.

My computer may have a faulty soundcard (integrated).

/dev/dsp is missing

no pipeline is set up to said soundcard

artsd is using the soundcard

You need to understand this first.  I am poor, I can't go spending money on frivolous things like xp, so I turn to this hoping that some kind soul out there will help me understand linux.  What I've seen so far, I like, I just wanna listen to my music...And also understand:

I HAVE NO IDEA OF EVEN WHERE TO START, I DO NOT KNOW WHAT I AM DOING.

---

### Post by mlind on 2006-03-18
ok, here's what I would do.

I'd make sure what's the brand/model of the integrated soundchip on the
motherboard. If you don't find this out using lshw, report-hw or other tools, see
your mobo manual or manufacturer's website.

If manufacturer is ESS like you said, see this [ALSA  soundcard matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix") for the
instructions, and the modules you may need to load manually.

When you get the correct module(s) loaded for the card, udev should recognize it,
and create /dev/dsp and /proc/asound/cards for you. Then use alsamixer to
unmute your channels and test playback using aplay.
/usr/share/sounds contains some clips to test with.

You must also have alsa-base alsa-utils libasound2 packages installed

---

### Post by cryptidan on 2006-03-18
> In a shell type these commands:

Make a directory to store the alsa source code in.

        cd /usr/src
        mkdir alsa
        cd alsa
        cp /downloads/alsa-* .

```
root@oldmine:/usr/src/alsa# cp /downloads/alsa-*
cp: missing destination file
Try `cp --help' for more information.
```

now what?

---

### Post by cryptidan on 2006-03-18
somebody, anybody, something, please.

---

### Post by mlind on 2006-03-18
[QUOTE=cryptidan]somebody, anybody, something, please.[/QUOTE]

You don't need to compile ALSA yourself.. It's provided by alsa-base package
that Ubuntu installs by default. You just need to modprobe right modules
if installer didn't correctly identify those.

---

### Post by therunnyman on 2006-03-18
Your pain is mine...

Okay, honestly, you know what I'd do?  Format and reinstall Ubuntu.  Stop there.  If you still don't have sound, we'll go through it step-by-step (and you probably won't have to open a terminal, even).

therunnyman

---

