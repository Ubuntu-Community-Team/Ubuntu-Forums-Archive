---
title: "iMac 2008 boot issue"
date: 2014-03-03
forum: Apple Hardware Users
---

### Post by Tony_Pickett on 2014-03-03
I 'inherited' a 2008 iMac from my wife recently after she upgraded her desktop machine.
I hated OSX, so I've wiped the drive and installed Xubuntu 13.10.
This is the hardware info:

24" iMac, 2.8GHz Core 2 Duo, 4GB SDRAM, 320GB Drive.
ATI Radeon HD 2600 PRO with 256MB of GDDR3 memory

The drive is partitioned as follows:
/dev/sda1 - fat32 - boot
/dev/sda4 - ?      - bios_grub
/dev/sda2 - ext4  - /
/dev/sda3 - swap - swap
/dev/sda5 - ext4  - /home

I'm pretty sure I have the boot screwed up, but it does boot however:

on turn on, it boots into GRUB2 in command line mode.
(I get the grub> prompt)

if I type exit, it closes and boots into rEFInd (I installed this in the mistaken believe that it was required)
Here I can select one of three options - two take me back to the GRUB command line and the third boots me into Xubuntu.
This machine is not dual booted, there is just Xubuntu and nothing else.

***What have I done wrong and what should I do to get this working correctly?***

---

