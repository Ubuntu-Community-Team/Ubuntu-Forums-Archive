---
title: "CD burner doesn't burn"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by yosarian on 2007-10-13
I have a CD burner Optorite CD-RW-CW4002 that works fine in Windows but it is not in Ubuntu. When I am using the K3b or the CD/DVD Writer GnomeBaker (or any other program) it doesn't write. 
When I want to copy a CD it stop in the 50% of the process just before the red light goes on and start the burning process.

Does anyone know what is the problem? Could be the Burner?

---

### Post by HermanAB on 2007-10-13
Underneath the glitz of all Linux CD programs, lies a couple of programs called mkisofs and cdrecord.  You have to find a howto on cdrecord and run it manually so that you can see the error messages.

BTW, try running K3B as root:
$ sudo -i
password
# k3b

Cheers,

Herman

---

### Post by yosarian on 2007-10-13
I run k3b as root and I got the errors I am posting in the next post. Can someone help me?

---

### Post by yosarian on 2007-10-13
and these

```


X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KService*): WARNING: Invalid Service : /usr/share/applications/Nessus.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
root@mc-desktop:~# (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_LG_CD_ROM_CRD_8522B to device /dev/hdd
Mapping udi /org/freedesktop/Hal/devices/storage_model_OPTORITE_CD_RW_CW4002 to device /dev/hdc
/dev/hdd resolved to /dev/hdd
/dev/hdd is block device (64)
/dev/hdd seems to be cdrom
(K3bDevice::Device) /dev/hdd: init()
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    GET CONFIGURATION (46)
                           errorcode:  70
                           sense key:  NOT READY (2)
                           asc:        3a
                           ascq:       0
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE with real length 65535 failed.
(K3bDevice::Device) /dev/hdd: modeSense 0x05 failed!
(K3bDevice::Device) /dev/hdd: Cannot check write modes.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/hdd: MODE SENSE with real length 65535 failed.
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems to be cdrom
(K3bDevice::Device) /dev/hdc: init()
(K3bDevice::Device) /dev/hdc feature: CD Mastering
(K3bDevice::Device) /dev/hdc feature: CD Track At Once
(K3bDevice::Device) /dev/hdc: dataLen: 60
(K3bDevice::Device) /dev/hdc: checking for TAO
(K3bDevice::Device) /dev/hdc: checking for SAO
(K3bDevice::Device) /dev/hdc: checking for SAO_R96P
(K3bDevice::Device) /dev/hdc: checking for SAO_R96R
(K3bDevice::Device) /dev/hdc: checking for RAW_R16
(K3bDevice::Device) /dev/hdc: checking for RAW_R96P
(K3bDevice::Device) /dev/hdc: checking for RAW_R96R
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        25
                           ascq:       0
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE length det failed.
(K3bDevice::Device) /dev/hdc:  Number of supported write speeds via 2A: 0
(K3bDevice::DeviceManager) setting current write speed of device /dev/hdc to 0
Devices:
------------------------------
Blockdevice:    /dev/hdd
Generic device: 
Vendor:         LG
Description:    CD-ROM CRD-8522B
Version:        2.02
Write speed:    0
Profiles:       Error
Read Cap:       CD-ROM
Write Cap:      Error
Writing modes:  None
Reader aliases: /dev/hdd
------------------------------
Blockdevice:    /dev/hdc
Generic device: 
Vendor:         OPTORITE
Description:    CD-RW CW4002
Version:        100E
Write speed:    0
Profiles:       CD-ROM, CD-R, CD-RW
Read Cap:       CD-ROM, CD-R, CD-RW
Write Cap:      CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R
Reader aliases: /dev/hdc
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kcmshell (kdelibs): WARNING: Could not find module 'k3bsetup2'.


```

---

### Post by yosarian on 2007-10-13
Running the k3b I got the following:

```

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
LG CD-ROM CRD-8522B 2.02 (/dev/hdd, ) [CD-ROM] [Error] [None]

OPTORITE CD-RW CW4002 100E (/dev/hdc, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]
Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'OPTORITE'
Identification : 'CD-RW CW4002    '
Revision       : '100E'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
Drive DMA Speed: 1075200 kB/s 6109x CD 776x DVD
FIFO size      : 12582912 = 12288 KB
Encoding speed : 305x (22864 sectors/s) for libedc from Heiko Eißfeldt
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
resid: 64512
Track 01: audio   16 MB (01:38.70) no preemp     
Track 02: audio   39 MB (03:55.00) no preemp     
Track 03: audio   55 MB (05:31.80) no preemp     
Track 04: audio   29 MB (02:52.66) no preemp     
Track 05: audio   25 MB (02:33.26) no preemp     
Track 06: audio   30 MB (02:58.73) no preemp     
Track 07: audio   47 MB (04:43.09) no preemp     
Track 08: audio   38 MB (03:49.33) no preemp     
Track 09: audio   53 MB (05:17.60) no preemp     
Track 10: audio   31 MB (03:09.04) no preemp     
Track 11: audio   18 MB (01:49.16) no preemp     
Track 12: audio   29 MB (02:56.04) no preemp     
Track 13: audio   13 MB (01:22.60) no preemp     
Track 14: audio   26 MB (02:35.09) no preemp     
Track 15: audio   46 MB (04:33.46) no preemp     
Track 16: audio   43 MB (04:20.10) no preemp     
Track 17: audio   21 MB (02:07.22) no preemp     
Track 18: audio   24 MB (02:26.93) no preemp     
Track 19: audio    9 MB (00:58.33) no preemp     
Track 20: audio   10 MB (01:05.24) no preemp     
resid: 4
resid: 2
resid: 4
resid: 2
/usr/X11R6/bin/wodim: Warning: controller returns zero sized CD write parameter page.
/usr/X11R6/bin/wodim: Warning: controller returns wrong size for CD write parameter page.
/usr/X11R6/bin/wodim: Warning: controller returns wrong page 0 for CD write parameter page (5).
/usr/X11R6/bin/wodim: Warning: controller returns zero sized CD write parameter page.
/usr/X11R6/bin/wodim: Warning: controller returns wrong size for CD write parameter page.
/usr/X11R6/bin/wodim: Warning: controller returns wrong page 0 for CD write parameter page (5).
/usr/X11R6/bin/wodim: Cannot init drive.
Track 21: audio   35 MB (03:32.16) no preemp     
Track 22: audio   87 MB (08:42.50) no preemp     
Total size:      736 MB (72:58.10) = 328358 sectors
Lout start:      736 MB (73:00/08) = 328358 sectors
Current Secsize: 539517301
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)

cdrecord command:
-----------------------
/usr/X11R6/bin/wodim -v gracetime=2 dev=/dev/hdc speed=32 -raw96r driveropts=burnfree -eject -text -useinfo -audio -shorttrack /tmp/kde-root/k3bCdCopy0/Track01.wav /tmp/kde-root/k3bCdCopy0/Track02.wav /tmp/kde-root/k3bCdCopy0/Track03.wav /tmp/kde-root/k3bCdCopy0/Track04.wav /tmp/kde-root/k3bCdCopy0/Track05.wav /tmp/kde-root/k3bCdCopy0/Track06.wav /tmp/kde-root/k3bCdCopy0/Track07.wav /tmp/kde-root/k3bCdCopy0/Track08.wav /tmp/kde-root/k3bCdCopy0/Track09.wav /tmp/kde-root/k3bCdCopy0/Track10.wav /tmp/kde-root/k3bCdCopy0/Track11.wav /tmp/kde-root/k3bCdCopy0/Track12.wav /tmp/kde-root/k3bCdCopy0/Track13.wav /tmp/kde-root/k3bCdCopy0/Track14.wav /tmp/kde-root/k3bCdCopy0/Track15.wav /tmp/kde-root/k3bCdCopy0/Track16.wav /tmp/kde-root/k3bCdCopy0/Track17.wav /tmp/kde-root/k3bCdCopy0/Track18.wav /tmp/kde-root/k3bCdCopy0/Track19.wav /tmp/kde-root/k3bCdCopy0/Track20.wav /tmp/kde-root/k3bCdCopy0/Track21.wav /tmp/kde-root/k3bCdCopy0/Track22.wav 


```

Also when I am trying to record some sound from a microphone to the computer, there is not input, is like the microphone doesn't work in Ubuntu (but it does in Windows)

---

### Post by yosarian on 2007-10-13
I run the k3b as root and the k3b now is not recognizing my CD burner as a burner device, please can someone help me?

---

### Post by paxmark1 on 2007-10-16
Note:  cdrecord is not the back end for k3b anymore in Debian flavours.  

wodim is.  Try and see if there is a difference between sudo wodim-scanbus versus sudo cdrecord-scanbus.  It uses growisofs for dvd's.  

All I can find for wodim is a man page and assorted talks in various forums.  It is not on sourceforge or freshmeat as Schilly's cdrecord  is.  

I had the exact same problems on my slim DVD-RW that is an APOS brand (cheapest slim laptop type for a small form function puter).  wodim did not like it for CD's and DVD's, but I have gotten it now to work for cd's.  

wodim has no problems with my LG external dvd-rw.

---

### Post by paxmark1 on 2007-10-16
also try 

cdrecord --version     and wodim --version

---

### Post by yosarian on 2007-10-22
> **paxmark1 said:**
> also try 

cdrecord --version     and wodim --version

I got

Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.2
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling

when I did wodim --version

and 

Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.2
Copyright (C) 2006 Cdrkit suite contributors

when I 
cdrecord --version

---

### Post by cfaulkner on 2007-10-22
I had this same problem.  I installed NeroLinux and i'm currently burning all my MST3k DVD's with it flawlessly.

---

### Post by yosarian on 2007-10-22
> **paxmark1 said:**
> Note:  cdrecord is not the back end for k3b anymore in Debian flavours.  

wodim is.  Try and see if there is a difference between sudo wodim-scanbus versus sudo cdrecord-scanbus.  It uses growisofs for dvd's.  

All I can find for wodim is a man page and assorted talks in various forums.  It is not on sourceforge or freshmeat as Schilly's cdrecord  is.  

I had the exact same problems on my slim DVD-RW that is an APOS brand (cheapest slim laptop type for a small form function puter).  wodim did not like it for CD's and DVD's, but I have gotten it now to work for cd's.  

wodim has no problems with my LG external dvd-rw.

How can I use wodim to burn?

---

