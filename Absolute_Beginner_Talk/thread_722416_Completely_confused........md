---
title: "Completely confused......."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by johngml on 2008-03-12
Installed Ubuntu 7.10 from a live disc three days ago and have spent many hours getting to grips with it and failing miserably.I love the idea of Linux and would love to be able to make full use of it. I have installed it on an 80Gb HD on a 2.8 Celeron with 256Mb Ram.

The problems I have are many but I will list them below.

1. Cannot find anyway to play music that is on a cd/dvd in folders. I don't want to put them on the computer, I just want to listen to them. In Windows this is easy but I cannot make it happen here. Even when I install the folders in my music folder I find that I cannot play them as they are MP3's and the GStreamer Extra Plugins will not install due to the same error mentioned below. I can see the Album Art of the music I cannot play though !

2. Trying to install any program is a nightmare. I am used to downloading and installing. I have not found any way to install the programs yet that explains it in plain english for somebody who is new to the operating system. ADD/Remove programs will not add anything that it lists. It comes up with a "Reload"" type message followed by a message that says "(program name) cannot be installed on your computer type (i386)." This happens on every single item.

3. I am trying to find a way of using email on the computer but I cannot get Evolution to work. I know I am not alone on that as I have seen loads of other people writing about it. I tried to install Thunderbird but I get the "cannot be installed on your computer type (i386)." error message. I downloaded it but could not get it to install in Terminal either as I got the same error. I tried Seamonkey but had the same problem.

4. I set a picture as wallpaper but next time I start the computer it is gone. The picture is in my pictures folder so I don't know why.. Is there something else I have to set ?

I am beginning to wonder if there are several types of Ubuntu and I have got a copy that doesn't like i386 computers. If there is anyone out there that could help me as I am getting a bit frustrated with it and I really would like to keep it on the computer as I have two others with Windows XP on and this does look pretty good.

---

### Post by Tobi-fp on 2008-03-12
Hey mate i would be glad to help.. But for everybody to find a way around, you should post all your problems in different threads.. Then people that searches theese problem, will easier find help..

---

### Post by finer recliner on 2008-03-12
did you install the 64-bit version of ubuntu?

---

### Post by alexforcefive on 2008-03-12
> **johngml said:**
> "(program name) cannot be installed on your computer type (i386)."

Have you somehow installed the 64 bit version of ubuntu? Is that even possible?

*edit* finer recliner beat me to it :D

---

### Post by jan quark on 2008-03-12
first open up the terminal and post the result of 
```

sudo lshw 
```

that we know your hardware and
```
uname -a
```

so that we know your ubuntu version

---

### Post by ByteJuggler on 2008-03-12
> **johngml said:**
> Installed Ubuntu 7.10 from a live disc three days ago and have spent many hours getting to grips with it and failing miserably.I love the idea of Linux and would love to be able to make full use of it. I have installed it on an 80Gb HD on a 2.8 Celeron with 256Mb Ram.


We'll do our best to help. :)

> **johngml said:**
> 
1. Cannot find anyway to play music that is on a cd/dvd in folders. I don't want to put them on the computer, I just want to listen to them. In Windows this is easy but I cannot make it happen here.


To confirm, what type of files are you trying to play?  MP3?  Or some other format?  (E.g. perhaps WMA, OGG...)

> **johngml said:**
> 
2. Trying to install any program is a nightmare. I am used to downloading and installing. I have not found any way to install the programs yet that explains it in plain english for somebody who is new to the operating system. ADD/Remove programs will not add anything that it lists. It comes up with a "Reload"" type message followed by a message that says "(program name) cannot be installed on your computer type (i386)." This happens on every single item.


That's very strange.  To clarify, you get Ubuntu built for 64-bit x86 computers (AMD64) and normal 32-bit x86 computers (i386.)  You cannot directly install 32-bit i386 packages onto a 64-bit installationand vice versa.  It won't work.  However, the Celeron didn't support 64-bit mode, unless you havea a very new Celeron with 64-bit extensions. Can you please clarify this, by opening up a Terminal (Applications->Accesories->Terminal) and then copying and pasting the following command into it:

```
cat /proc/cpuinfo
```

Then copy and paste the output here.  (Use the "Edit" menu to copy/paste, or use Shift-Ctrl C and Shift-Ctrl-v inside the Terminal and just Ctrl-C and Ctrl-V in othre applications.)


> **johngml said:**
> 
3. I am trying to find a way of using email on the computer but I cannot get Evolution to work. I know I am not alone on that as I have seen loads of other people writing about it. I tried to install Thunderbird but I get the "cannot be installed on your computer type (i386)." error message. I downloaded it but could not get it to install in Terminal either as I got the same error. I tried Seamonkey but had the same problem.


What exactly is going wrong with Evolution?  I'll ignore the Thunderbird problem until we've figured out what's wrong with your computer re installing sofware.

> **johngml said:**
> 
4. I set a picture as wallpaper but next time I start the computer it is gone. The picture is in my pictures folder so I don't know why.. Is there something else I have to set ?


Exactly what are you doing when you set the wallpaper?

---

### Post by petercoh7 on 2008-03-12
I'm wondering if the Celeron processor is supported ?

---

### Post by finer recliner on 2008-03-12
> **petercoh7 said:**
> I'm wondering if the Celeron processor is supported ?

all mainstream intel/AMD 32-bit processors are backwards compatible with the i386 processor architecture, which is the default kernel that is installed with ubuntu. so, yes, it is supported.

---

### Post by Tom--d on 2008-03-12
> 
2. Trying to install any program is a nightmare. I am used to downloading and installing. I have not found any way to install the programs yet that explains it in plain english for somebody who is new to the operating system. ADD/Remove programs will not add anything that it lists. It comes up with a "Reload"" type message followed by a message that says "(program name) cannot be installed on your computer type (i386)." This happens on every single item. 

Easy to fix!

What I did was..

System > Admin > Software sources 

Check every box sept 'Source Code' and Installing from CD/DVD.

Then On the tabs above, go to updates and its really self explanatory there :)

This should stop this and you can now install software (I had the exact problem as you)
Hope this helps!

Edit: 

> 
3. I am trying to find a way of using email on the computer but I cannot get Evolution to work. I know I am not alone on that as I have seen loads of other people writing about it. I tried to install Thunderbird but I get the "cannot be installed on your computer type (i386)." error message. I downloaded it but could not get it to install in Terminal either as I got the same error. I tried Seamonkey but had the same problem.

After, you should be able to install Thunderbird :)

And with the CD playing. It will ask you to download codecs. Download then and it will automatically install them. This will fix your problems.

---

### Post by johngml on 2008-03-12
So many replies, don't know where to start. Entering " sudo lshw" gives me this :-

john-desktop              
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: SiS-661
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (03/01/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: Socket 775
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc up pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 256MB
          capacity: 2GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             slot: A0
             size: 256MB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: SCSI Disk
                product: Maxtor 6Y080L0
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y20RTSYC
                size: 76GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 75GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 627MB
                   capacity: 627MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 627MB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVDRW SHW-160P6S
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PS05
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:16:ec:34:69:6e
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_sis latency=32 module=sata_sis
        *-network:1
             description: Wireless interface
             product: AR5212/AR5213 Multiprotocol MAC/baseband processor
             vendor: Atheros Communications, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: wifi0
             version: 01
             serial: 00:14:6c:8c:87:9d
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.0.4 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
john@john-desktop:~$ 

Does that help ?

---

### Post by johngml on 2008-03-12
Entering " cat /proc/cpuinfo gives me this :-

john@john-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Celeron(R) CPU 2.80GHz
stepping        : 9
cpu MHz         : 2806.545
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc up pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 5616.91
clflush size    : 64

john@john-desktop:~$ 

With regards to the wallpaper, I go into the pictures folder, open the picture I want and then click on "Image" followed by "Set as wallpaper".

---

### Post by johngml on 2008-03-12
The version of Ubuntu that I installed was a version 7.10 Live disc. I do not think that it would have been a 64 instead of a 32 but to be honest, I do not think that was an option.

---

### Post by johngml on 2008-03-12
The command  "uname -a" gives me this as my version :-
john@john-desktop:~$ uname -a
Linux john-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
john@john-desktop:~$

---

### Post by bjdodo on 2008-03-12
Just a quick question: did you boot into ubuntu without the cd? I am asking because the background picture stuff. Did you remove the live cd and tried to start your computer without the cd?

---

### Post by johngml on 2008-03-12
In Evolution I get this error when I try to use it :-
MAIL FROM command failed: Must issue a STARTTLS command first r38sm1237774ugc.55

The music I want to play is MP3's but I cannot install the GStreamer Extra plugins due to the same error I get on the other programs.

---

### Post by johngml on 2008-03-12
I have actually installed Ubuntu and do not use the disc at all.
Thanks.

---

### Post by Tom--d on 2008-03-12
> **johngml said:**
> In Evolution I get this error when I try to use it :-
MAIL FROM command failed: Must issue a STARTTLS command first r38sm1237774ugc.55

The music I want to play is MP3's but I cannot install the GStreamer Extra plugins due to the same error I get on the other programs.


Do what I said a few posts back and try to install the GStreamer. 

Tell me if it worked :)

---

### Post by johngml on 2008-03-12
Done it and it now works but all the MP3's keep breaking up about every 3 seconds. Any idea what is causing that as they worked fine on this computer under XP ?

---

### Post by Chris555 on 2008-03-12
breaking up is rather generic description
is the sound distorting every 3 seconds or is the music pausing every 3 seconds

you are at the lower limits for running Gutsy with 256 megs of ram. You could be having a buffer problem with the minimal ram.

---

### Post by johngml on 2008-03-12
Sussed the music. When I went into the music folder and clicked on the song I wanted it was actually being opened by Totem. I have now gone into Rhymbox and imported all the songs and it works great. 
Thank you very much for help.

---

### Post by Tom--d on 2008-03-12
How about updates? have they worked...

Can you install any other software?

---

### Post by johngml on 2008-03-13
Hi Tom--d,
Sorry for the wait but I have been out. I can confirm that updates are working fine as does everything else. I just wish I had known about those settings in the beginning.

I am very grateful for your help and everybody else's as well. I did not expect such quick replies or so many. I think I can safetly say that it wouldn't have been like that on a windows forum. I would have got replies but not so many and definately not so quick. I have a funny feeling that Ubuntu will be staying put on this computer and may just sneak on one or two others..........

---

