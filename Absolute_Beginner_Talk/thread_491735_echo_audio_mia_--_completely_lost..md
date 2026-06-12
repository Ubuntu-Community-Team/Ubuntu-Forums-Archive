---
title: "echo audio mia -- completely lost."
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by robb. on 2007-07-04
i've had some stability issues with my echo audio mia soundcard in windows XP lately, so i'd like to get over that last hurdle to making this system as usable as my windows partition.  sure, i could use the internal audio for basic web-surfing audio and .mp3 listening, which seems to work automatically, but i'd rather make it work with the mia.

unfortunately, as much as i am a competent computer user, i'm not much of a software person.  i've been to the [EchoMia wiki](https://help.ubuntu.com/community/EchoMia), but part of my confusion is that i can use synaptic to install the ALSA drivers, right?  or is my problem that i need to install it by hand?

i know ubuntu recognizes the card.  in my device manager, it properly identifies the motorola DSP chip used by echo, and identifies echo as the vendor of the card:

[quote=device manager]Vendor: Motorola
Product: DSP 56361 Digital Signal Processor
OEM Vendor: Echo Digital Audio Corporation
OEM Product: Mia rev.0[/quote]

what's the next step?  do i download the tarball and learn the hard way how to install packages by hand?  can i configure it some way since i have some ALSA drivers already and ubuntu knows the card is there?

any help?

thanks.

robb.

---

### Post by robb. on 2007-07-05
noob question = noob answer, i guess.

in case anyone else is looking, my searches have yielded a few results that i will be trying in the next few days.  first, there is [this  guide at the alsa projet site](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Mia-midi.&chip=Motorola+56361&module=mia).  i also read that ubuntu studio automatically recognizes the mia.  that may be preferable for me, since i'd like to try recording in linux.

robb.

---

### Post by pekko on 2007-07-10
If you are running Feisty, you should have alsa driver 1.0.13 installed by default. Firmware for Echo Audio cards is not distributed with Feisty, so you will have to compile it from source. Try this:

```
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.14rc3.tar.bz2
tar -xjvf alsa-firmware-1.0.14rc3.tar.bz2
cd alsa-firmware-1.0.14rc3
./configure
make
sudo make install
sudo modprobe snd-mia
cat /proc/asound/cards
```

These packages need to be installed before compiling:
build-essential
gettext
libncurses5-dev
libncursesw5-dev

---

### Post by robb. on 2007-07-10
thanks for the reply, pekko.  i decided to get over my fear of command prompt and compile the drivers.  i ran into an issue when i tried ./configure, but i think you might have directed me to the root cause.  when i ran tar, i used -xf, not -x**j**vf.  this prompted me to look into what the -j flag does.  i imagine adding the -j bzip flag changes how the data is decompressed.

i was running into an issue where when i tried the command ./configure --with-cards=mia --with-oss=yes --with-sequencer=yes couldn't recognize some files.  i haven't received any responses to my pleas on that yet, but i will try tar -xjvf and see if that doesn't fix the error.

thanks!

robb.

---

### Post by pekko on 2007-07-11
Most likely you have a missing dependency. Have you checked that you have all the packages installed that I mentioned in my earlier message? You might also need to install linux-headers package for the kernel version you are using.

You can search the packages by name in synaptic if you are not sure if everything is installed or not.

br Pekko

---

### Post by robb. on 2007-07-11
i'm installing the other dependency packages right now.  then i'll try to re-unzip the driver and install per the directions.  hopefully it'll work.

thanks for your help!  i actually started reading linuxcommand.org to make sure i learn how this stuff works and so i won't be so confused in the future.  it's been a while since i've learned UNIX commands, and i know linux isn't exactly the same.

robb.

---

### Post by robb. on 2007-07-12
it works!  thanks a million for your help!

robb.

---

### Post by bricksen on 2007-08-11
hallo maybe you could help me alittle aswell?
I run the 7.04 dist and got the mia-midi version of the same card with motorola 56361 chip

I installed both driver and lib packages without any trouble but when i came to configuering the utils package i resieved this message:

checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.

I did a:

sudo apt-get install build-essential ncurses-dev gettext

and

sudo apt-get install linux-headers-`uname -r`

before install
Where can i find this libasound? didn't i get that with the lib-package?
A bit confused here? :-)

BET

---

### Post by schorsch on 2007-08-11
I guess you have to install the libasound development package:

```
sudo apt-get install libasound2-dev 
```

---

### Post by bricksen on 2007-08-11
Thanks for such å quick answer and that got me one step further :KS

I now did:

modprobe snd-mia;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

returned with no messages. But when i try to start alsamixer i get this:

alsamixer: function snd_ctl_open failed for default: No such device

but i find it in /usr/bin ???? Then i tried to reconfigure utils and see this message:

config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting

Has this anything to do with the problem? I tried to do a new "make" and got :

aplay.c: In function &#8216;pcm_list&#8217;:
aplay.c:274: warning: assignment makes pointer from integer without a cast

one place and:

aplay.o: In function `pcm_list':
/usr/src/alsa/alsa-utils-1.0.14/aplay/aplay.c:269: undefined reference to `snd_device_name_hint'

further down, and this at the end:

collect2: ld returned 1 exit status
make[1]: *** [aplay] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make: *** [all-recursive] Error 1

I just tried a "make install" too and that ended with:

/usr/src/alsa/alsa-utils-1.0.14/aplay/aplay.c:300: undefined reference to `snd_device_name_free_hint'
collect2: ld returned 1 exit status
make[1]: *** [aplay] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make: *** [install-recursive] Error 1

of course but what is this aplay nonsens :confused:
by the way aplay -l only returned this : **** List of PLAYBACK Hardware Devices ****

---

### Post by schorsch on 2007-08-11
O.K.  I was able to reproduce the error. Right at the moment I have no idea what is the reason for this, but why do you not try the official version of the alsa-utils in the repositories? These should work with your card, the only thing that is missing is the firmware and the installation of the firmware is described a few posts before.

---

### Post by bricksen on 2007-08-11
does that mean that it's in this ubuntu from start  ?
and how do i get rid of all the things from this failed installation?

---

### Post by schorsch on 2007-08-11
Yip, it's all there, only with another version (1.0.13):

```
~$ apt-cache search alsa | grep ^alsa
alsa-base - ALSA driver configuration files
alsa-utils - ALSA utilities
alsa-oss - ALSA wrapper for OSS applications
alsa-source - ALSA driver sources
alsa-tools - Console based ALSA utilities for specific hardware
alsa-tools-gui - GUI based ALSA utilities for specific hardware
alsamixergui - graphical soundcard mixer for ALSA soundcard driver
alsaplayer-alsa - PCM player designed for ALSA (ALSA output module)
alsaplayer-common - PCM player designed for ALSA (common files)
alsaplayer-daemon - PCM player designed for ALSA (non-interactive version)
alsaplayer-esd - PCM player designed for ALSA (EsounD output module)
alsaplayer-gtk - PCM player designed for ALSA (GTK version)
alsaplayer-jack - PCM player designed for ALSA (JACK output module)
alsaplayer-nas - PCM player designed for ALSA (NAS output module)
alsaplayer-oss - PCM player designed for ALSA (OSS output module)
alsaplayer-text - PCM player designed for ALSA (text version)
alsaplayer-xosd - PCM player designed for ALSA (osd version)
alsa-firmware-loaders - ALSA software loaders for specific hardware

```

As you were not able to do a proper make to compile the alsa-utils, there should be nothing to do. But to be on the safe side change your directory to the you wanted to compile the alsa-utils and do

```
make uninstall
```

After that you can delete the directory.
If you have installed the other packages in the same way, you can try this for them, too. Otherwise I would just reinstall the packages from the repos and if you are getting errors, do an uninstall and then a reinstall again.

---

### Post by bricksen on 2007-08-11
Is there any chance i can just install the and the utils from repos and skip the uninstall of the new driver and lib?
Is it comp back in time?

---

### Post by schorsch on 2007-08-11
Have you checked if it is not already installed?

```
dpkg -l|grep alsa
```

In this case you would have updated some files already probably. But keep in mind, that any future update of the alsa packages could overwrite some of your compiled files. Right at this moment I would try to work with the official packages plus the mentioned firmware file (if you are still having problems) as described above.
Also mixing different subversions may work sometimes, but it is not guaranteed to work after some updates. Keep as close to the repos as you can and you are quite safe.

---

### Post by ThrashJazzAssassin on 2007-08-11
Theres a package in the ubuntustudio repos that made my echoaudio darla card work straight away without having to compile anything. I think its a firmware package.

---

### Post by bricksen on 2007-08-11
Thanx alot for answering so fast on my questions :KS:KS

I tried rename and "make uninstall" but that ended with unable to log in to pc with a dependencie fault from libasound :confused: So i did a reinstall of the os.
Now i installed alsamixergui and ended up with a:

alsamixer:function snd_cti_open failed for default: No such device

and then i did a: dpkg -l|grep alsa  and got this:

ii  alsa-base                                  1.0.13-3ubuntu1                        ALSA driver configuration files
ii  alsa-utils                                 1.0.13-1ubuntu5                        ALSA utilities
ii  alsamixergui                               0.9.0rc2-1-9                           graphical soundcard mixer for ALSA soundcard
ii  gstreamer0.10-alsa                         0.10.12-0ubuntu1                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.36-3ubuntu4                        Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa                         1.10.3-0ubuntu1                        Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                       1.2.11-7ubuntu1                        Simple DirectMedia Layer (with X11 and ALSA 

So I really dont understand why it cant show my card in system/prferences/sound menu?
It has already installed the drivers??? alsaconf is missing thu...

PS unable to find eny firmware under repos?

---

### Post by schorsch on 2007-08-11
o.k., now go back to page one of this thread and read post number three. The firmware is not in the repos, but I have the checked the procedure as described in post #3.
I was able to compile everything but could not test as I do not own such a sound card.

---

### Post by bricksen on 2007-08-11
Everything went nicely with the install but when i did: cat /proc/asound/cards
i got:

 1 [UM1            ]: USB-Audio - UM-1
                      EDIROL UM-1 at usb-0000:00:10.1-1, full speed

thats a usb midi device for my keyboard but no soundcard
and still no alsaconf

when i look closer i see:

make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bricksen/alsa-firmware-1.0.14rc3'
make[1]: Leaving directory `/home/bricksen/alsa-firmware-1.0.14rc3'

can this be right?

---

### Post by schorsch on 2007-08-11
o.k., when you did the modprobe line where there any messages? And what is the Output of the commands "dmesg" and "lspci"? Don't worry about the four lines you mentioned, these are normal messages.

---

### Post by bricksen on 2007-08-11
none with modprobe

bricksen@bricksen:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000005fefc000 end: 000000005fffc000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000005fffc000 size: 0000000000003000 end: 000000005ffff000 type: 3
[    0.000000] copy_e820_map() start: 000000005ffff000 size: 0000000000001000 end: 0000000060000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fffc000 (usable)
[    0.000000]  BIOS-e820: 000000005fffc000 - 000000005ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ffff000 - 0000000060000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 393212) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393212
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393212
[    0.000000] On node 0 totalpages: 393212
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1279 pages used for memmap
[    0.000000]   HighMem zone: 162557 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5fb0
[    0.000000] ACPI: RSDT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc000
[    0.000000] ACPI: FADT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc0b2
[    0.000000] ACPI: BOOT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc030
[    0.000000] ACPI: MADT (v001 ASUS   A7V8X    0x42302e31 MSFT 0x31313031) @ 0x5fffc058
[    0.000000] ACPI: DSDT (v001   ASUS A7V8X    0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] Detected 1800.231 MHz processor.
[   23.649221] Built 1 zonelists.  Total pages: 390141
[   23.649226] Kernel command line: root=UUID=7df55828-790d-4c10-893b-2a005636ed09 ro quiet splash
[   23.649413] mapped APIC to ffffd000 (fee00000)
[   23.649416] mapped IOAPIC to ffffc000 (fec00000)
[   23.649420] Enabling fast FPU save and restore... done.
[   23.649423] Enabling unmasked SIMD FPU exception support... done.
[   23.649436] Initializing CPU#0
[   23.649511] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.654844] Console: colour VGA+ 80x25
[   23.655796] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.657377] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.729241] Memory: 1548088k/1572848k available (1992k kernel code, 23584k reserved, 900k data, 328k init, 655344k highmem)
[   23.729253] virtual kernel memory layout:
[   23.729255]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.729256]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.729257]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.729259]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.729260]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   23.729262]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   23.729263]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   23.729267] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.805285] Calibrating delay using timer specific routine.. 3602.30 BogoMIPS (lpj=7204601)
[   23.805344] Security Framework v1.0.0 initialized
[   23.805357] SELinux:  Disabled at boot.
[   23.805379] Mount-cache hash table entries: 512
[   23.805597] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   23.805608] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[   23.805613] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.805616] CPU: L2 Cache: 256K (64 bytes/line)
[   23.805619] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   23.805635] Compat vDSO mapped to ffffe000.
[   23.805643] Remapping vsyscall page to ffffe000
[   23.805658] Checking 'hlt' instruction... OK.
[   23.821458] SMP alternatives: switching to UP code
[   23.821835] Freeing SMP alternatives: 11k freed
[   23.822154] Early unpacking initramfs... done
[   24.165393] ACPI: Core revision 20060707
[   24.166262] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.170010] CPU0: AMD Athlon(TM) XP 2200+ stepping 01
[   24.170036] Total of 1 processors activated (3602.30 BogoMIPS).
[   24.170236] ENABLING IO-APIC IRQs
[   24.170428] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.316599] Brought up 1 CPUs
[   24.316906] Booting paravirtualized kernel on bare hardware
[   24.317002] Time: 17:45:53  Date: 07/11/107
[   24.317050] NET: Registered protocol family 16
[   24.317181] EISA bus registered
[   24.317186] ACPI: bus type pci registered
[   24.318544] PCI: PCI BIOS revision 2.10 entry at 0xf1720, last bus=1
[   24.318547] PCI: Using configuration type 1
[   24.318549] Setting up standard PCI resources
[   24.333420] ACPI: Interpreter enabled
[   24.333427] ACPI: Using IOAPIC for interrupt routing
[   24.334125] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   24.334342] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   24.334554] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   24.334766] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   24.335071] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14) *9
[   24.335341] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[   24.335447] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.335454] PCI: Probing PCI hardware (bus 00)
[   24.335774] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   24.336385] PCI quirk: region e400-e47f claimed by vt8235 PM
[   24.336389] PCI quirk: region e800-e80f claimed by vt8235 SMB
[   24.336553] Boot video device is 0000:01:00.0
[   24.336597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.338049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   24.342731] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.342748] pnp: PnP ACPI init
[   24.347222] pnp: PnP ACPI: found 14 devices
[   24.347228] PnPBIOS: Disabled by ACPI PNP
[   24.347307] PCI: Using ACPI for IRQ routing
[   24.347311] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.351491] NET: Registered protocol family 8
[   24.351493] NET: Registered protocol family 20
[   24.351778] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[   24.351782] pnp: 00:02: ioport range 0xe800-0xe81f could not be reserved
[   24.351798] pnp: 00:0d: ioport range 0x290-0x291 has been reserved
[   24.351801] pnp: 00:0d: ioport range 0x370-0x372 has been reserved
[   24.352132] PCI: Bridge: 0000:00:01.0
[   24.352135]   IO window: disabled.
[   24.352141]   MEM window: dd000000-dfdfffff
[   24.352145]   PREFETCH window: dff00000-efffffff
[   24.352165] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.352202] NET: Registered protocol family 2
[   24.388556] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.388852] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.391102] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.392249] TCP: Hash tables configured (established 131072 bind 65536)
[   24.392255] TCP reno registered
[   24.400606] checking if image is initramfs... it is
[   25.042873] Freeing initrd memory: 6787k freed
[   25.043121] Simple Boot Flag at 0x3a set to 0x1
[   25.043507] audit: initializing netlink socket (disabled)
[   25.043528] audit(1186854353.476:1): initialized
[   25.043614] highmem bounce pool size: 64 pages
[   25.043692] VFS: Disk quotas dquot_6.5.1
[   25.043724] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.043802] io scheduler noop registered
[   25.043806] io scheduler anticipatory registered
[   25.043809] io scheduler deadline registered
[   25.043817] io scheduler cfq registered (default)
[   25.044119] isapnp: Scanning for PnP cards...
[   25.397105] isapnp: No Plug & Play device found
[   25.432409] Real Time Clock Driver v1.12ac
[   25.432481] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.432603] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.432876] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.433709] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.434124] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.434471] mice: PS/2 mouse device common for all mice
[   25.435194] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.435507] input: Macintosh mouse button emulation as /class/input/input0
[   25.435547] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.435552] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.435824] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.439480] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.439490] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.439704] EISA: Probing bus 0 at eisa.0
[   25.439742] EISA: Detected 0 cards.
[   25.469814] TCP cubic registered
[   25.469821] NET: Registered protocol family 1
[   25.469852] Using IPI No-Shortcut mode
[   25.469927] ACPI: (supports S0 S1 S4 S5)
[   25.469974]   Magic number: 3:876:794
[   25.470153]   hash matches device ptyr2
[   25.470710] Freeing unused kernel memory: 328k freed
[   25.470847] Time: tsc clocksource has been installed.
[   25.487346] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.752653] Capability LSM initialized
[   27.396338] ieee1394: Initialized config rom entry `ip1394'
[   27.397927] PCI: Enabling device 0000:00:07.0 (0094 -> 0097)
[   27.397945] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 17 (level, low) -> IRQ 16
[   27.450855] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[dc800000-dc8007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   27.472853] SCSI subsystem initialized
[   27.478805] libata version 2.20 loaded.
[   27.480145] sata_promise 0000:00:08.0: version 2.01
[   27.480171] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 17 (level, low) -> IRQ 16
[   27.480188] sata_promise PATA port found
[   27.512206] ata1: SATA max UDMA/133 cmd 0xf887a200 ctl 0xf887a238 bmdma 0x00000000 irq 16
[   27.512251] ata2: SATA max UDMA/133 cmd 0xf887a280 ctl 0xf887a2b8 bmdma 0x00000000 irq 16
[   27.526487] usbcore: registered new interface driver usbfs
[   27.526520] usbcore: registered new interface driver hub
[   27.526551] usbcore: registered new device driver usb
[   27.527707] USB Universal Host Controller Interface driver v3.0
[   27.533368] ata3: PATA max UDMA/133 cmd 0xf887a300 ctl 0xf887a338 bmdma 0x00000000 irq 16
[   27.533387] scsi0 : sata_promise
[   27.847313] ata1: SATA link down (SStatus 0 SControl 300)
[   27.847341] scsi1 : sata_promise
[   28.162844] ata2: SATA link down (SStatus 0 SControl 0)
[   28.162869] scsi2 : sata_promise
[   28.322865] tg3.c:v3.72 (January 8, 2007)
[   28.322891] PCI: Enabling device 0000:00:09.0 (0014 -> 0016)
[   28.322904] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 17
[   28.370309] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:e0:18:b9:16:92
[   28.370319] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[   28.370322] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[   28.370517] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[   28.370537] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   28.370755] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   28.370790] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000b400
[   28.370974] usb usb1: configuration #1 chosen from 1 choice
[   28.371015] hub 1-0:1.0: USB hub found
[   28.371030] hub 1-0:1.0: 2 ports detected
[   28.478611] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 18
[   28.478631] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   28.478674] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   28.478705] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000b000
[   28.478855] usb usb2: configuration #1 chosen from 1 choice
[   28.478893] hub 2-0:1.0: USB hub found
[   28.478906] hub 2-0:1.0: 2 ports detected
[   28.586418] PCI: Enabling device 0000:00:10.2 (0014 -> 0015)
[   28.586434] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
[   28.586451] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   28.586498] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   28.586529] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000a800
[   28.586651] usb usb3: configuration #1 chosen from 1 choice
[   28.586683] hub 3-0:1.0: USB hub found
[   28.586695] hub 3-0:1.0: 2 ports detected
[   28.694351] PCI: Enabling device 0000:00:10.3 (0014 -> 0016)
[   28.694364] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 18
[   28.694386] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   28.694427] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   28.694488] ehci_hcd 0000:00:10.3: irq 18, io mem 0xda000000
[   28.694495] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.694594] usb usb4: configuration #1 chosen from 1 choice
[   28.694626] hub 4-0:1.0: USB hub found
[   28.694643] hub 4-0:1.0: 6 ports detected
[   28.734332] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800000b126b]
[   28.804514] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   28.804541] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   28.804544] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   28.804556] VP_IDE: chipset revision 6
[   28.804559] VP_IDE: not 100% native mode: will probe irqs later
[   28.804571] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   28.804581]     ide0: BM-DMA at 0xa400-0xa407, BIOS settings: hda:DMA, hdb:DMA
[   28.804597]     ide1: BM-DMA at 0xa408-0xa40f, BIOS settings: hdc:DMA, hdd:DMA
[   28.804607] Probing IDE interface ide0...
[   29.225351] hda: WDC WD1200JB-75CRA0, ATA DISK drive
[   29.508929] hdb: ST3400832A, ATA DISK drive
[   29.570610] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.583614] Probing IDE interface ide1...
[   29.836359] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   30.003310] usb 2-1: configuration #1 chosen from 1 choice
[   30.139994] hdc: PLEXTOR DVDR PX-712A, ATAPI CD/DVD-ROM drive
[   30.423571] hdd: WDC WD3200JB-00KFA0, ATA DISK drive
[   30.483714] ide1 at 0x170-0x177,0x376 on irq 15
[   30.496791] hda: max request size: 128KiB
[   30.516068] hda: Host Protected Area detected.
[   30.516072]  current capacity is 234375000 sectors (120000 MB)
[   30.516074]  native  capacity is 234441648 sectors (120034 MB)
[   30.519517] hda: Host Protected Area disabled.
[   30.519527] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   30.519536] hda: cache flushes not supported
[   30.519613]  hda: hda1 hda3 < hda5 hda6 hda7 >
[   30.576345] hdb: max request size: 512KiB
[   30.576447] hdb: 781422768 sectors (400088 MB) w/8192KiB Cache, CHS=48641/255/63, UDMA(100)
[   30.576537] hdb: cache flushes supported
[   30.576575]  hdb: hdb1
[   30.594315] hdd: max request size: 512KiB
[   30.594397] hdd: 625142448 sectors (320072 MB) w/8192KiB Cache, CHS=38913/255/63, UDMA(33)
[   30.594496] hdd: cache flushes supported
[   30.594519]  hdd: hdd1
[   30.631212] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)
[   30.631227] Uniform CD-ROM driver Revision: 3.20
[   31.033892] Attempting manual resume
[   31.033898] swsusp: Resume From Partition 3:6
[   31.033900] PM: Checking swsusp image.
[   31.034075] PM: Resume from disk failed.
[   31.066399] kjournald starting.  Commit interval 5 seconds
[   31.066418] EXT3-fs: mounted filesystem with ordered data mode.
[   40.281179] PM: Writing back config space on device 0000:00:09.0 at offset b (was 164714e4, writing 80a91043)
[   40.281195] PM: Writing back config space on device 0000:00:09.0 at offset 3 (was 0, writing 4008)
[   40.281201] PM: Writing back config space on device 0000:00:09.0 at offset 2 (was 2000000, writing 2000002)
[   40.281207] PM: Writing back config space on device 0000:00:09.0 at offset 1 (was 2b00000, writing 2b00006)
[   40.281212] PM: Writing back config space on device 0000:00:09.0 at offset 0 (was 164714e4, writing 16a614e4)
[   41.982969] NET: Registered protocol family 17
[   42.578777] tg3: eth0: Link is up at 10 Mbps, half duplex.
[   42.578783] tg3: eth0: Flow control is off for TX and off for RX.
[   42.743572] Linux agpgart interface v0.102 (c) Dave Jones
[   42.995700] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.998399] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.349683] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   43.359237] agpgart: AGP aperture is 128M @ 0xf0000000
[   43.423774] irda_init()
[   43.423806] NET: Registered protocol family 23
[   43.636950] parport: PnPBIOS parport detected.
[   43.637004] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   43.657641] input: PC Speaker as /class/input/input2
[   43.909791] logips2pp: Detected unknown logitech mouse model 62
[   44.021984] PCI: Enabling device 0000:00:0b.0 (0014 -> 0016)
[   44.022004] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   44.142882] usbcore: registered new interface driver snd-usb-audio
[   44.204783] get_firmware(): Firmware not available (-2)
[   44.204828] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[   44.204848] Echoaudio Mia: probe of 0000:00:0b.0 failed with error -2
[   44.376519] fuse init (API version 7.8)
[   44.408815] lp0: using parport0 (interrupt-driven).
[   44.432408] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   44.537724] Adding 979924k swap on /dev/disk/by-uuid/ea21f190-95dc-4d3b-882e-23081202b0b2.  Priority:-1 extents:1 across:979924k
[   44.695517] EXT3 FS on hda7, internal journal
[   44.810004] NET: Registered protocol family 10
[   44.810129] lo: Disabled Privacy Extensions
[   45.009011] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   45.079435] NTFS volume version 3.1.
[   45.125076] NTFS volume version 3.1.
[   45.158759] NTFS volume version 3.1.
[   45.192898] NTFS volume version 3.1.
[   50.732035] Using specific hotkey driver
[   50.824629] No dock devices found.
[   50.886014] ibm_acpi: ec object not found
[   50.973133] input: Power Button (FF) as /class/input/input4
[   50.978928] ACPI: Power Button (FF) [PWRF]
[   51.017462] input: Power Button (CM) as /class/input/input5
[   51.023218] ACPI: Power Button (CM) [PWRB]
[   51.128165] pcc_acpi: loading...
[   56.915957] ppdev: user-space parallel port driver
[   57.618602] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   57.618610] apm: overridden by ACPI.
[   57.825058] Bluetooth: Core ver 2.11
[   57.825154] NET: Registered protocol family 31
[   57.825157] Bluetooth: HCI device and connection manager initialized
[   57.825162] Bluetooth: HCI socket layer initialized
[   57.880823] Bluetooth: L2CAP ver 2.8
[   57.880829] Bluetooth: L2CAP socket layer initialized
[   57.977180] Bluetooth: RFCOMM socket layer initialized
[   57.977203] Bluetooth: RFCOMM TTY layer initialized
[   57.977205] Bluetooth: RFCOMM ver 1.8
[   72.764653] eth0: no IPv6 routers present

bricksen@bricksen:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
00:09.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
00:0b.0 Multimedia controller: Motorola DSP56361 Digital Signal Processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)


And I used synaptic to see what packages there were:
alsa-base 1.0.13-3ubuntu1 (marked green and "orange")
alsa-firmware-loaders 1.0.13-1
alsa-mixergui 0.9.0rc2-1-9 (marked green)
alsa-oss 1.0.12-1
alsa-player-alsa 0.99.76.9
alsa-common  0.99.76.9
alsa-deamon  0.99.76.9
alsa-esd  0.99.76.9
alsa-gtk  0.99.76.9
alsa-jack  0.99.76.9
alsa-nas  0.99.76.9
alsa-source 1.0.13-3ubuntu1
alsa-tools 1.0.13-1
alsa-tools-gui 1.0.13-1
alsa-utils 1.0.13-1ubuntu5  (marked green and "orange")

Lot of different versions and all of them was installed auto at install of oss?
hope this tells you anything and thanx that you use your time to help me :KS

---

### Post by schorsch on 2007-08-11
o.k., first of all:

green means: Software is already installed
orange (the Ubuntu Logo): will be installed per default.

Now for the rest: I guess the follwing lines in the dmesg-output are causing some trouble:

[44.204783] get_firmware(): Firmware not available (-2)
[ 44.204828] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[ 44.204848] Echoaudio Mia: probe of 0000:00:0b.0 failed with error -2

The Firmware file is not found.

lspci lists your chip, thats fine.

Ah, I guess I found something: I compiled the firmware again and installed it. Afterwards I found the firmware files in /lib/firmware, but as far as I know they have to be installed in /lib/firmware/'uname -r' where 'uname -r' just returns the version of the current kernel. So on my machine firmware files for the running kernel are located under /lib/firmware/2.6.20-16-generic.

Could you please change back to the directory in which you compiled the firmware before and:
```

make distclean
./configure --with-hotplug-dir='/lib/firmware/'uname -r'/'
make
sudo make install
ls -l /lib/firmware/'uname -r'/ea/mia_dsp.fw

```

mia_dsp.fw should be the firmware file

---

### Post by bricksen on 2007-08-11
sorry dinnertime :)

bricksen@bricksen:~/alsa-firmware-1.0.14rc3$ ./configure --with-hotplug-dir='/lib/firmware/'uname -r'/'
configure: error: unrecognized option: -r/
Try `./configure --help' for more information.

It didn't understand the command

---

### Post by schorsch on 2007-08-11
hmmm ...... the command is not resolved by configure. 

Please do:

```
ls -d /lib/firmware/`uname -r`
```

and put the output of this command as here typed as XXX

```
 ./configure --with-hotplug-dir='XXX'
```

Then go on as mentioned before

---

### Post by bricksen on 2007-08-11
I'm sorry to say that i can't find anything called alsa under /lib/firmware or /lib/firmware/2.6.20-16-generic?

---

### Post by schorsch on 2007-08-11
You will not find anything with alsa there; only firmware files ending with .fw are stored there. And I guess the relevant file for you is mia_dsp.fw.

Ah, you can call configure by

```
./configure --with-hotplug-dir='/lib/firmware/2.6.20-16-generic'
```

---

### Post by bricksen on 2007-08-11
bricksen@bricksen:~/alsa-firmware-1.0.14rc3$ sudo ls -d /lib/firmware/`uname -r`/lib/firmware/2.6.20-16-generic

bricksen@bricksen:~/alsa-firmware-1.0.14rc3$ ./configure --with-hotplug-dir='XXX'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
./configure: line 3318: ./version: Permission denied
checking for as31... no
checking firmware installation directory... XXX
configure: creating ./config.status
config.status: creating Makefile
config.status: creating hdsploader/Makefile
config.status: creating mixartloader/Makefile
config.status: creating usx2yloader/Makefile
config.status: creating vxloader/Makefile
config.status: creating pcxhrloader/Makefile
config.status: creating echoaudio/Makefile
config.status: creating emi_26_62/Makefile
config.status: creating emu/Makefile
config.status: creating asihpi/Makefile
config.status: creating korg1212/Makefile
config.status: creating maestro3/Makefile
config.status: creating multisound/Makefile
config.status: creating sb16/Makefile
config.status: creating wavefront/Makefile
config.status: creating ymfpci/Makefile
config.status: executing depfiles commands

---

### Post by bricksen on 2007-08-11
no mia_dsp.fw either

sorry it's under /lib/firmware/ea/

---

### Post by schorsch on 2007-08-11
Sorry, that was a little bit ..... 

```
./configure --with-hotplug-dir='/lib/firmware/2.6.20-16-generic'
make
sudo make install
```

---

### Post by bricksen on 2007-08-11
still

[   44.204783] get_firmware(): Firmware not available (-2)
[   44.204828] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[   44.204848] Echoaudio Mia: probe of 0000:00:0b.0 failed with error -2

---

### Post by schorsch on 2007-08-11
You did a reboot, right? Is the file "mia_dsp.fw" now available under "/lib/firmware/2.6.20-16-generic/ea" or still under "/lib/firmware/ea"?

---

### Post by bricksen on 2007-08-11
sorry had to reboot
but still under.....
no it's in both :-)

---

### Post by schorsch on 2007-08-11
Ah, ok, in both ...... then please type:

```
rmmod snd-mia
modprobe snd-mia
dmesg | tail -20

```

and post this output please.

---

### Post by bricksen on 2007-08-11
:KS:KS:KS

[   36.411990] PCI: Enabling device 0000:00:0b.0 (0014 -> 0016)
[   36.412009] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   36.642135] Card registered: Mia rev.1 (DSP56361) at 0xda800000 irq 19

:guitar:     :popcorn:

Thanks alot there still are some issues with the control volume applet (runs wild when picked on but still works)  and unable to control volume with xmms.

---

### Post by schorsch on 2007-08-11
Ah, so you say that the card is working now? Great!

But keep two things in mind:

- After a kernel update the firmware probably has to be compiled again, so keep the sources (the directory) and perhaps the instructions I gave you!

- You do not have to reboot every time you change something; that is windows behaviour :) 

As I do not use this kind of sound card I am not able to guide for your new questions .... and in the meantime I did a little research on your card and Ubuntu on google ... with quite few answers :(

Perhaps you should buy another sound card with better linux support but which one ...... I don't know ...

---

### Post by bricksen on 2007-08-11
Changed in xmms and was abel to turn up the volume with the applet so everythings perfect

My man hope this thread can help many others too, see alot of confusion around echo hardware strange that they haven't come up with their own drivers for linux yet and are so little GPL in their ways :confused: Nice cards thoug... I use it mostly to play keyboard and bass and record the mess :)

really really apreciate what you did.

---

### Post by schorsch on 2007-08-11
Hey, I am a bass player, too (we have to stand together, firmly and upright!) ..... but I do not record to my laptop.

The problem with your card was not the driver but the firmware. Normally the hardware should have an intelligent chip, that has the basic commands burned in. But it is cheaper to do this via software. When running such hardware under windows the windows driver has the intelligence and controls the card, but not the hardware itself. So from now on, every time you boot there is some kind of software flashing the sound card. And this is really a problem of the hardware designers as they do not open the driver sources to the community as you already mentioned!

But I am glad to hear that it is now working on your side and keep in mind: Keep the sources and  my instructions as that compiling could be necessary again after an update!

And perhaps in a few months you will be able to support others, too! That's the purpose of this community..... and it works!

Enjoy your music ..... and Ubuntu ... and have a pleasant weekend!

---

