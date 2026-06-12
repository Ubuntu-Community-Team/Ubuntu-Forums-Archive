---
title: "K3B constantly crashes on a fresh gutsy install"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by djrobthaman on 2007-10-21
Hi everybody,

Just a quick question.  K3B won't load on my fresh guutsy install and I was wondering if anyone else was having the same problem and had already figured out a solution.

Thanks for the info, and here is the terminal output:

```

douglas@douglas-desktop:~$ k3b
douglas@douglas-desktop:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_CE_SW_CW4103____ to device /dev/scd1
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD_RW_16XMax to device /dev/scd0
/dev/scd1 resolved to /dev/scd1
/dev/scd1 is block device (1)
/dev/scd1 seems to be cdrom
bus: 6, id: 1, lun: 0
(K3bDevice::Device) /dev/scd1: init()
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::Device) /dev/scd1 feature: DVD Read (pre-MMC5)
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::Device) /dev/scd1 feature: BD Read
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::Device) /dev/scd1 feature: Layer Jump Recording
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       1
KCrash: Application 'k3b' crashing...

```

---

### Post by dogstar1 on 2008-02-12
I am having similar problems.

I am running:

[COLOR="DarkOrange"]Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu **2.6.22-14.51-generic**)[/COLOR]

Various dmesg:

[COLOR="DarkOrange"]ata2.01: ATAPI: LITE-ON DVDRW LH-20A1L, BL05, max UDMA/100
ata2.01: configured for UDMA/100
ata2.00: configured for UDMA/100
ata2.01: configured for UDMA/33
ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
ata2: failed to recover some devices, retrying in 5 secs
ata2.01: qc timeout (cmd 0xa0)
ata2.01: ATAPI check failed
ata2: soft resetting port
ata2: port is slow to respond, please be patient (Status 0xd0)
ata2: device not ready (errno=-16), forcing hardreset
ata2.01: 16 bytes trailing data[/COLOR]

hdparm output:

[COLOR="DarkOrange"]/dev/dvdrw:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device[/COLOR]

sdparm output:

[COLOR="DarkOrange"] /dev/dvdrw
    /dev/dvdrw: LITE-ON   DVDRW LH-20A1L    BL05  [cd/dvd]
Read write error recovery mode page:
  AWRE        1  [cha: y, def:  1]
  ARRE        1  [cha: y, def:  1]
  PER         0  [cha: y, def:  0]
Write parameters (MMC) mode page:
  BUFE        1  [cha: n, def:  1]
  WR_T        0  [cha: y, def:  0]
  MULTI_S     0  [cha: y, def:  0]
[/COLOR]

hdparm -c1 -u1 -d1 -a1 /dev/dvd

[COLOR="DarkOrange"]/dev/dvd:
 setting fs readahead to 1
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting unmaskirq to 1 (on)
 HDIO_SET_UNMASKINTR failed: Inappropriate ioctl for device
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support    =  0 (default 16-bit)
 readahead     =  0 (off)[/COLOR]


/proc/modules

[COLOR="DarkOrange"]nls_iso8859_1 5120 1 - Live 0xf8ea6000
nls_cp437 6784 1 - Live 0xf8e7b000
vfat 14080 1 - Live 0xf8ea1000
fat 54300 1 vfat, Live 0xf8f91000
fglrx 656352 29 - Live 0xf8ff4000 (P)
ppdev 10244 0 - Live 0xf8e5b000
ipv6 273892 22 - Live 0xf8eac000
cpufreq_ondemand 9612 0 - Live 0xf8e57000
cpufreq_conservative 8072 0 - Live 0xf8e4c000
cpufreq_userspace 5280 0 - Live 0xf8e4f000
cpufreq_powersave 2688 0 - Live 0xf8908000
cpufreq_stats 7232 0 - Live 0xf8b09000
freq_table 5792 2 cpufreq_ondemand,cpufreq_stats, Live 0xf8b0c000
ac 6148 0 - Live 0xf8aa5000
video 18060 0 - Live 0xf8b1b000
dock 10656 0 - Live 0xf8b17000
sbs 19592 0 - Live 0xf8b11000
container 5504 0 - Live 0xf8aa8000
button 8976 0 - Live 0xf8af5000
battery 11012 0 - Live 0xf8a6b000
aes_i586 34304 0 - Live 0xf8aeb000
dm_crypt 14984 0 - Live 0xf8ae6000
dm_mod 58816 1 dm_crypt, Live 0xf8af9000
parport_pc 37412 0 - Live 0xf8ace000
lp 12580 0 - Live 0xf8ab2000
parport 37448 3 ppdev,parport_pc,lp, Live 0xf8adb000
loop 19076 0 - Live 0xf8aac000
snd_hda_intel 263712 2 - Live 0xf8b23000
snd_pcm_oss 44672 0 - Live 0xf8a84000
snd_pcm 80388 2 snd_hda_intel,snd_pcm_oss, Live 0xf8ab9000
snd_mixer_oss 17664 1 snd_pcm_oss, Live 0xf8a9a000
snd_seq_dummy 4740 0 - Live 0xf8a77000
snd_seq_oss 33152 0 - Live 0xf8a90000
snd_seq_midi 9600 0 - Live 0xf8a73000
snd_rawmidi 25728 1 snd_seq_midi, Live 0xf8a7c000
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi, Live 0xf8a6f000
snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf8a34000
snd_timer 24324 2 snd_pcm,snd_seq, Live 0xf8a64000
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf8a29000
af_packet 24840 2 - Live 0xf8a5c000
pcspkr 4224 0 - Live 0xf8a31000
psmouse 39952 0 - Live 0xf8a51000
snd 54660 13 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf8a42000
soundcore 8800 1 snd, Live 0xf8a2d000
iTCO_wdt 11940 0 - Live 0xf89bb000
iTCO_vendor_support 4868 1 iTCO_wdt, Live 0xf8a26000
usblp 15104 0 - Live 0xf8978000
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm, Live 0xf89b7000
serio_raw 8068 0 - Live 0xf89b4000
shpchp 34580 0 - Live 0xf8a1c000
pci_hotplug 32704 1 shpchp, Live 0xf89d2000
intel_agp 25620 0 - Live 0xf89ca000
agpgart 35016 2 fglrx,intel_agp, Live 0xf89c0000
evdev 11136 3 - Live 0xf8981000
usb_storage 73024 1 - Live 0xf8990000
ide_core 116804 1 usb_storage, Live 0xf89fe000
ext3 133896 5 - Live 0xf89dc000
jbd 60456 1 ext3, Live 0xf89a4000
mbcache 9732 1 ext3, Live 0xf897d000
libusual 18448 1 usb_storage, Live 0xf883d000
sg 36764 0 - Live 0xf8932000
sr_mod 17828 0 - Live 0xf8918000
cdrom 37536 1 sr_mod, Live 0xf8985000ftp://ftp.berlios.de/pub/cdrecord/mkisofs/00MESSAGE
sd_mod 30336 13 - Live 0xf896f000
sbp2 24072 1 - Live 0xf8968000
usbhid 29536 0 - Live 0xf895f000
hid 28928 1 usbhid, Live 0xf893c000
ata_piix 17540 5 - Live 0xf8912000
ohci1394 36528 1 - Live 0xf8928000
ieee1394 96312 2 sbp2,ohci1394, Live 0xf8946000
ehci_hcd 36492 0 - Live 0xf891e000
uhci_hcd 26640 0 - Live 0xf890a000
usbcore 138632 7 usblp,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd, Live 0xf889b000
ata_generic 8452 0 - Live 0xf8897000
libata 125168 2 ata_piix,ata_generic, Live 0xf88e1000
scsi_mod 147084 6 usb_storage,sg,sr_mod,sd_mod,sbp2,libata, Live 0xf8851000
e1000 126272 0 - Live 0xf8877000
thermal 14344 0 - Live 0xf8843000
processor 32072 1 thermal, Live 0xf8848000
fan 5764 0 - Live 0xf883a000
fuse 47124 1 - Live 0xf8821000
apparmor 40728 0 - Live 0xf882f000
commoncap 8320 1 apparmor, Live 0xf881d000
[/COLOR]

K3B output: (snipped)

[COLOR="DarkOrange"]
(K3bDevice::Device) /dev/scd1READ TRACK INFORMATION for DVD-ROM failed.
DiskInfo:
Mediatype:       CD-ROM
Current Profile: DVD-R Sequential
Disk state:      unknown
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        00:00:01 (LBA 1) (2048 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       00:00:01 (LBA 1) (2048 Bytes)

                           command:    READ CAPACITY (25)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       2
(K3bDevice::ScsiCommand) failed:
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       2
(K3bDevice::Device) /dev/scd1: READ TRACK INFORMATION length det failed.
(K3bDevice::ScsiCommand) failed:
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       2
(K3bDevice::Device) /dev/scd1: READ TRACK INFORMATION with real length 36 failed.
(K3bDevice::Device) /dev/scd1READ TRACK INFORMATION for DVD-ROM failed.
DiskInfo:
Mediatype:       CD-ROM
Current Profile: DVD-R Sequential
Disk state:      unknown
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        00:00:01 (LBA 1) (2048 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       00:00:01 (LBA 1) (2048 Bytes)
[/COLOR]

Here are some links I investigated along the way:

[Link01]("http://tinyurl.com/253656")
[Link02]("http://tinyurl.com/yo236n")
[Link03]("http://tinyurl.com/2grc3v")

---

