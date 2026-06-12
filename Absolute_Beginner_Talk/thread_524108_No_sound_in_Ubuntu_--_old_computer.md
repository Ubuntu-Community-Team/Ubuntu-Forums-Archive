---
title: "No sound in Ubuntu -- old computer"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2007-08-12
I just got an old computer (450MHz, 256M RAM) and Ubuntu got installed successfully onto it. However, it seems like there are no sound devices it can recognize. I am not even sure there is one because the place where it should be is not accessible (I'll have to disassemble other hardware in order to see it), but the three jacks at the back (Input, Output, Microphone) are present. Is there any way I could make this work?

---

### Post by bren on 2007-08-12
run the command

> lshw -short 

in a terminal and post here

bren

---

### Post by NT4.0 on 2007-08-12
----------------------------

H/W path                     Device     Class      Description
==============================================================
                                        system     OptiPlex GX1 450Mbr+
/0                                      bus        Motherboard
/0/0                                    memory     BIOS
/0/400                                  processor  Pentium III (Katmai)
/0/400/700                              memory     L1 cache
/0/400/701                              memory     L2 cache
/0/1000                                 memory     System Memory
/0/1000/0                               memory     DIMM DRAM Synchronous
/0/1000/1                               memory     DIMM DRAM Synchronous
/0/1000/2                               memory     DIMM DRAM Synchronous [empty]
/0/f0000000                             bridge     440BX/ZX/DX - 82443BX/ZX/DX Host bridge
/0/f0000000/1                           bridge     440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
/0/f0000000/1/0                         display    3D Rage Pro AGP 1X/2X
/0/f0000000/7                           bridge     82371AB/EB/MB PIIX4 ISA
/0/f0000000/7.1                         storage    82371AB/EB/MB PIIX4 IDE
/0/f0000000/7.1/0            ide0       bus        IDE Channel 0
/0/f0000000/7.1/0/0          /dev/hda   disk       WDC WD102AA
/0/f0000000/7.1/0/0/1        /dev/hda1  disk       Linux filesystem partition
/0/f0000000/7.1/0/0/2        /dev/hda2  disk       Linux swap / Solaris partition
/0/f0000000/7.1/0/0/3        /dev/hda3  disk       Linux filesystem partition
/0/f0000000/7.1/1            ide1       bus        IDE Channel 1
/0/f0000000/7.1/1/0          /dev/hdc   disk       SAMSUNG CD-ROM SC-140F
/0/f0000000/7.1/1/0/0        /dev/hdc   disk       
/0/f0000000/7.2                         bus        82371AB/EB/MB PIIX4 USB
/0/f0000000/7.2/1            usb1       bus        UHCI Host Controller
/0/f0000000/7.2/1/1          scsi0      storage    USB Mass Storage Device
/0/f0000000/7.2/1/1/0.0.0    /dev/sda   disk       MHV2100AH
/0/f0000000/7.2/1/1/0.0.0/1  /dev/sda1  disk       Linux filesystem partition
/0/f0000000/7.3                         bridge     82371AB/EB/MB PIIX4 ACPI
/0/f0000000/e                           display    NV4 [RIVA TNT]
/0/f0000000/f                           bridge     DECchip 21152
/0/f0000000/11               eth0       network    3c905B 100BaseTX [Cyclone]

----------------------------

I found the pages where people were having a similar problem:

[http://ubuntuforums.org/showthread.php?t=305269&highlight=gx1+audio](http://ubuntuforums.org/showthread.php?t=305269&highlight=gx1+audio)
[http://www.linuxquestions.org/questions/showthread.php?t=217353](http://www.linuxquestions.org/questions/showthread.php?t=217353)

the modprobe command worked, at least i hear the slight noise in the earphones plugged in the jack, so at least I know I do have a sound card and it must be connected, but there is no sound (the sound files play but the sound is absent).

EDIT: I appended 

snd-cs4236

to /etc/modules and now the system starts up with the volume control active. Still, the sound files play but I don't hear anything.

---

