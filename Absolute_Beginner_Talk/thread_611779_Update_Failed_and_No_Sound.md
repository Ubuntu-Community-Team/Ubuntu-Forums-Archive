---
title: "Update Failed and No Sound"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Clawson on 2007-11-13
Hello everyone, i'm new at this (apparant because of where i'm posting this) and i had two errors with the new installation of Ubuntu on my laptop.  First off it is a Toshiba P105-S6197, it has a Intel Core 2 Duo T5200 and Intel Graphics Chip.

After installed Ubuntu, nearly everything worked right off of the bat.  I was suprised to see my wireless even working.  However i have no sound.  No Beeps, no .wav sounds, nothing.  I was wondering where i should go next to fix this problem.

Next, i decided to run the update manager to see if it would fix this problem, or just basically upgrade the system.  When i ran the update manager i got this error.

E: tzdata: subprocess post-installation script returned error exit status 10

Can anyone help?

Thanks!
Matt

---

### Post by FuturePilot on 2007-11-13
For the sound can you post the output of 
```
lspci
```
Go Applications>Accessories>Terminal and put that in there.

---

### Post by Clawson on 2007-11-13
Here you go, thanks!

matt@matt-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
matt@matt-laptop:~$

---

### Post by FuturePilot on 2007-11-13
Here's your sound card
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```
There's been some problems with this card, however some have had luck with this
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Add this to the bottom
```
options snd-hda-intel position_fix=1 model=3stack"
```
Save the file and reboot.

---

### Post by Clawson on 2007-11-13
i added the line to the file and rebooted.  Still nothing.  Could it be related to my problem with updating?

Matt

---

### Post by FuturePilot on 2007-11-13
No, the update problem is not related to the sound.

---

### Post by Clawson on 2007-11-13
I went through and tried to copy and paste this but it wouldn't let me.  So i typed it out

Extracting templeates from packages: 100%
Preconfiguring packages...
setting up tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error processing tzdata --(configure):bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tzdata (2007h-0ubuntu0.7.10)  ...
dpkg: error processing tzdata (--configure):
subprocess post-installation script returned error exit status 10
Errors were enountered while processing
tzdata





Matt

---

### Post by Clawson on 2007-11-13
Here is the entire alsa-base file for your viewing pleasure.  Maybe something in there i typed in goofed.

Matt

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel position_fix=1 model=3stack"

---

