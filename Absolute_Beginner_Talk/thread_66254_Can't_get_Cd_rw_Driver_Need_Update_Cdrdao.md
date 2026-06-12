---
title: "Can't get Cd rw Driver? Need Update Cdrdao"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by sunshine82 on 2005-09-16
Hi I am new to Ubuntu. 

I have installed cdrdao 1.1.9.3 but 
the driver i need Sony Crx140e is on cdrdao 2.0 
I have been to the cdrdao website and have attempt
 to download it from there but that did not work 
what should I do  

](*,)  ](*,)  ](*,)  ]

---

### Post by mlomker on 2005-09-16
> I have installed cdrdao 1.1.9.3 but 
the driver i need Sony Crx140e is on cdrdao 2.0 


1.2 is the latest version.  My CDR's have all worked with the included version.  Why does your Sony need the newer ones?  

Are you saying you couldn't download it or you couldn't figure out how to compile it?

---

### Post by sunshine82 on 2005-09-16
I mean I cant hear the music 
, the music from the cd is playing 
but nothing is coming out the speaker.
 I can not compile it?
I have check what devices are on cdrdao 1.1.9 
but sony crx140e is not on it .
And you are right it is 1.2

---

### Post by mlomker on 2005-09-16
CDRDAO is a support program for writing CD's (burning them).  It doesn't have anything to do with playing CD's.  

Do you have sound in other programs--like playing MP3 files?

---

### Post by sunshine82 on 2005-09-25
I do nt have sound in anything ? when I cdrdao scan bus it say :

ERROR: Cannot open SCSI device '/dev/cdrecorder': Cannot open '/dev/cdrecorder'
Supported SCSI transports for this platform:

Transport name:         sg
Transport descr.:       Generic transport independent SCSI
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         pg
Transport descr.:       SCSI transport for ATAPI over Parallel Port
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport
Transp. layer ind.:     ATAPI:
Target specifier:       bus,target,lun
Target example:         ATAPI:1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport using sg interface
Transp. layer ind.:     ATA:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported
ERROR: Please use option '--device [proto:]bus,id,lun', e.g. --device 0,6,0 or --device ATAPI:0,0,0
ERROR: Cannot setup device /dev/cdrecorder

---

### Post by mlomker on 2005-09-25
> I do nt have sound in anything ? when I cdrdao scan bus it say :

ERROR: Cannot open SCSI device '/dev/cdrecorder': Cannot open '/dev/cdrecorder'
Supported SCSI transports for this platform:


It looks like the system isn't seeing your CD-ROM drive at all.  Can you read CD's in that drive?  I assume it is a newer SATA drive?

For your sound problem you will have to start by determining if the driver is loaded.  **lspci** will give you a list of devices and one of them should be the chipset of the sound card.  After that you can type **lsmod | more** to see if the driver is loaded.  There are a few [troubleshooting](http://linux.iuplog.com/default.asp?item=94639) guides once you are sure that the driver is loading.

---

### Post by sunshine82 on 2005-09-25
This the responds when I 
lspci:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:09.0 Communication controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
0000:00:0b.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

---

### Post by mlomker on 2005-09-25
> 
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)

That's the one.  Try **lsmod | grep snd**.

---

### Post by sunshine82 on 2005-09-25
this is the responsd from  lsmod | grep snd:


snd_ymfpci             56384  0
snd_opl3_lib            9856  1 snd_ymfpci
snd_hwdep               8608  1 snd_opl3_lib
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  1
gameport               14472  2 snd_ymfpci,snd_via82xx
snd_ac97_codec         72188  2 snd_ymfpci,snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_ymfpci,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  4 snd_ymfpci,snd_opl3_lib,snd_seq,snd_pcm
snd_page_alloc         10120  3 snd_ymfpci,snd_via82xx,snd_pcm
snd_mpu401_uart         6784  2 snd_ymfpci,snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  16 snd_ymfpci,snd_opl3_lib,snd_hwdep,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd

---

