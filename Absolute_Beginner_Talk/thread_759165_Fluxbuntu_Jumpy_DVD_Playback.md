---
title: "Fluxbuntu Jumpy DVD Playback"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by joeyt2k on 2008-04-18
Thinkpad 1400i , Celeron 366, 192 MB of RAM running Fluxbuntu 7.10. DVD-ROM is stock, used to play DVDs perfectly in Windows 98 when I got it ... in 1999. 

I've tried every DVD player I can think of, currently futzing with VLC -- nothing I adjust makes a DVD watchable. Video/audio are very jumpy.

I've tried tutorials on enabling DMA, but that doesn't work (DMA won't turn on, a common problem apparently). I've tried other players, that doesn't work. I've got more RAM on the way but I don't know if the jump to 256 MB is going to help much. 

The magic of Ubuntu has made this ten-year-old box totally usable in every other aspect, any help fixing this or links to discussions I missed would be greatly appreciated.

---

### Post by warbread on 2008-04-19
I'm not finding anything on google about people not being able to turn on DMA on this particular laptop.  Are you sure it's that common?  What did you try?  What did it say?

DMA is most certainly the issue, IMO.  You simple can't watch DVDs without it.  Unless, I suppose, you cached a huge chunk before starting the film, but that would take forever to get started.

---

### Post by joeyt2k on 2008-04-19
Thank you for your reply.

A couple guides said to do hdparm -d1 /dev/cdrom or /dev/hdc but when I do that I get:

/dev/cdrom (or hdc):
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off)

I also read that I should edit my /etc/hdparm.conf file. Currently, after all the commented lines, there is an entry that reads:

/dev/hdc {
dma = on
}

For that, all I get is the same "HDIO_SET_DMA failed: Operation not permitted" message when I boot (Fluxbuntu loads fasted for me when I turn off the bootsplash).

I don't know if this matters, but I have the same problem with Flash/YouTube videos in Firefox/Seamonkey, but I just assumed that was because the CPU doesn't meet Flash's minimum requirements. 

Any ideas?

---

### Post by warbread on 2008-04-20
Please understand that I'm not being condesending when I ask this, but have you yet tried 

```

**sudo** hdparm -d1 /dev/cdrom

```

yet?  

Though, it seems to be a moot point as editing hdparm.conf gave the same result.

Also, see what 'hdparm -a' gives you.  That may be interesting.

---

### Post by joeyt2k on 2008-04-20
Yes, using sudo.

hdparm -a:

hdparm - get/set hard disk parameters - version v7.5

Usage:  hdparm  [options] [device] ..

Options:
 -a   get/set fs readahead
 -A   get/set the drive look-ahead flag (0/1)
 -b   get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   set Advanced Power Management setting (1-255)
 -c   get/set IDE 32-bit IO setting
 -C   check drive power mode status
 -d   get/set using_dma flag
 -D   enable/disable drive defect management
 -E   set cd-rom drive speed
 -f   flush buffer cache for device on exit
 -g   display drive geometry
 -h   display terse usage information
 -H   read temperature from drive (Hitachi only)
 -i   display drive identification
 -I   detailed/current information directly from drive
 -k   get/set keep_settings_over_reset flag (0/1)
 -K   set drive keep_features_over_reset flag (0/1)
 -L   set drive doorlock (0/1) (removable harddisks only)
 -M   get/set acoustic management (0-254, 128: quiet, 254: fast)
 -m   get/set multiple sector count
 -n   get/set ignore-write-errors flag (0/1)
 -p   set PIO mode on IDE interface chipset (0,1,2,3,4,...)
 -P   set drive prefetch count
 -q   change next setting quietly
 -Q   get/set DMA tagged-queuing depth (if supported)
 -r   get/set device  readonly flag (DANGEROUS to set)
 -R   register an IDE interface (DANGEROUS)
 -s   set power-up in standby flag (0/1) (DANGEROUS)
 -S   set standby (spindown) timeout
 -t   perform device read timings
 -T   perform cache read timings
 -u   get/set unmaskirq flag (0/1)
 -U   un-register an IDE interface (DANGEROUS)
 -v   defaults; same as -acdgkmur for IDE drives
 -V   display program version and exit immediately
 -w   perform device reset (DANGEROUS)
 -W   get/set drive write-caching flag (0/1)
 -x   tristate device for hotswap (0/1) (DANGEROUS)
 -X   set IDE xfer mode (DANGEROUS)
 -y   put drive in standby mode
 -Y   put drive to sleep
 -Z   disable Seagate auto-powersaving mode
 -z   re-read partition table
 --direct         use O_DIRECT to bypass page cache for timings
 --Istdin         read identify data from stdin as ASCII hex
 --Istdout        write identify data to stdout as ASCII hex
 --verbose        display extra diagnostics from some commands
 --security-help  display help for ATA security commands
 --drq-hsm-error  crash system with a "stuck DRQ" error (VERY DANGEROUS)

---

### Post by joshrobinson on 2008-04-20
could you post the following

```
lspci -v
```
and
```
lsmod
```

---

### Post by joeyt2k on 2008-04-20
**lspci -v**
00:00.0 Host bridge: ALi Corporation M1621 (rev 05)
        Flags: bus master, slow devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [b0] AGP version 1.0

00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01) (prog-if 00 [
Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 80500000-80cfffff
        Prefetchable memory behind bridge: 80d00000-820fffff

00:06.0 Communication controller: Agere Systems WinModem 56k (rev 01)
        Subsystem: AMBIT Microsystem Corp. Lucent Win Modem
        Flags: bus master, medium devsel, latency 0, IRQ 9
        Memory at 80100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 7090 [size=8]
        I/O ports at 7400 [size=256]
        Capabilities: [f8] Power Management version 2

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/
V+] (rev 0a)
        Subsystem: Acer Incorporated [ALI] Unknown device 1002
        Flags: bus master, medium devsel, latency 0

00:08.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (re
v 02)
        Subsystem: ESS Technology Unknown device 8898
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at 7800 [size=64]
        I/O ports at 7850 [size=16]
        I/O ports at 7870 [size=16]
        I/O ports at 7890 [size=4]
        I/O ports at 78a4 [size=4]
        Capabilities: [c0] Power Management version 1

00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20) (prog-if 8a [Master Se
cP PriP])
        Flags: bus master, medium devsel, latency 32, IRQ 15
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size
=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size
=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size
=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size
=1]
        I/O ports at 78c0 [size=16]

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] (rev 09)
        Subsystem: Acer Incorporated [ALI] Unknown device 1002
        Flags: medium devsel

00:13.0 CardBus bridge: O2 Micro, Inc. OZ6832/6833 CardBus Controller (rev 34)
        Subsystem: Acer Incorporated [ALI] Unknown device 1002
00:13.0 CardBus bridge: O2 Micro, Inc. OZ6832/6833 CardBus Controller (rev 34)
        Subsystem: Acer Incorporated [ALI] Unknown device 1002
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 9
        Memory at 20000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10000000-13fff000 (prefetchable)
        Memory window 1: 14000000-17fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

00:13.1 CardBus bridge: O2 Micro, Inc. OZ6832/6833 CardBus Controller (rev 34)
        Subsystem: Acer Incorporated [ALI] Unknown device 1002
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 9
        Memory at 20001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 18000000-1bfff000 (prefetchable)
        Memory window 1: 1c000000-1ffff000
        I/O window 0: 00001c00-00001cff
        I/O window 1: 00002000-000020ff
        16-bit legacy interface ports at 0001

00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 
[OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at 82100000 (32-bit, non-prefetchable) [size=4K]

01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV
] (rev 20) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 1002
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at 81000000 (32-bit, prefetchable) [size=16M]
        Memory at 80800000 (32-bit, non-prefetchable) [size=4M]
        Memory at 80500000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [dc] Power Management version 1


--------------------------------------------------------------------------

**lsmod**
Module                  Size  Used by
apm                    22744  2 
af_packet              24840  2 
lp                     12708  0 
loop                   19204  0 
ipv6                  272612  8 
aes                    28864  1 
airo_cs                 7424  1 
snd_es1938             23940  0 
gameport               16776  2 snd_es1938
airo                   74780  1 airo_cs
snd_opl3_lib           11776  1 snd_es1938
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_es1938
snd_pcm_oss            44800  0 
snd_pcm                80644  2 snd_es1938,snd_pcm_oss
snd_page_alloc         11656  1 snd_pcm
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_dummy           4996  0 
parport_pc             37540  1 
pcmcia                 41516  1 airo_cs
snd_seq_oss            33536  0 
snd_seq_midi            9728  0 
parport                37704  2 lp,parport_pc
snd_rawmidi            25856  2 snd_mpu401_uart,snd_seq_midi
psmouse                40208  0 
pcspkr                  4352  0 
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
i2c_ali1535             8452  0 
i2c_ali15x3             9220  0 
i2c_core               26240  2 i2c_ali1535,i2c_ali15x3
snd_seq                53488  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          9484  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8324  0 
yenta_socket           27660  4 
rsrc_nonstatic         14336  1 yenta_socket
pcmcia_core            41236  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd                    54916  12 snd_es1938,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8928  1 snd
ali_agp                 8320  1 
agpgart                35272  1 ali_agp
shpchp                 34836  0 
pci_hotplug            32960  1 shpchp
evdev                  11392  1 
ext3                  134024  1 
jbd                    59688  1 ext3
mbcache                 9860  1 ext3
usbhid                 29664  0 
hid                    29056  1 usbhid
ide_cd                 32672  0 
cdrom                  37792  1 ide_cd
ide_disk               18688  3 
ata_generic             8708  0 
libata                125168  1 ata_generic
scsi_mod              147212  1 libata
floppy                 60004  0 
ohci_hcd               23044  0 
usbcore               138504  3 usbhid,ohci_hcd
alim15x3               12684  0 [permanent]
generic                 6020  0 [permanent]
ide_core              113604  4 ide_cd,ide_disk,alim15x3,generic
fuse                   46996  1 
fbcon                  41888  0 
tileblit                3712  1 fbcon
font                    9472  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3456  1 bitblit

---

### Post by j21a2t89 on 2008-07-17
have you tried caching on vlc.
file>>open disc at the bottom click caching and enter something like 12000 it will the cache the first 12 that your about to watch.

---

