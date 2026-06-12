---
title: "Ubuntu Ultimate 1.4 --- 3 days, No sound"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by gbc65 on 2007-09-17
here's the scoop.
 
i've checked all the volume controls i could find for mutes. the command $ lspci turns up :```
 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
I am running the Linux Kernel 2.6.20-16-generic, which SHOULD provide the drivers for the Intel audio chip-set.
i found the following solution
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
and believe i followed it correctly, still no sound.
 
the following is a link to the specs of my machine
[http://209.167.114.38/support/TechSupport/productcontents/satellite/PSPA3C-JR500E.htm](http://209.167.114.38/support/TechSupport/productcontents/satellite/PSPA3C-JR500E.htm)
 
Can anyone suggest something else for me to try?
tia
gbc65

---

### Post by CaptainInsaneO on 2007-09-17
Go into your BIOS and disable the hd audio. Your soundcard is a Conexant.

Next, go into Ubuntu. System>Preferences (I believe)>Volume Control, and change your default device to your sound card.

I have this problem and it's driven me crazy in the past, this is how I fixed it :)

---

### Post by gbc65 on 2007-09-20
```
 
CONFIGURATION 

To Enter:F2, Boot Option: F12To Flash:Self Boot DiskDMI:Satellite P100TSETUP Default Settings: [LEFT]PHOENIX BIOS (out of the box settings)[/LEFT]

 
(Press F2 to Enter)
Info.
  CPU Type: Genuine Intel (R) CPU T2400 @ 1.83GHz
  CPU Speed: 1833 MHz
  HDD Model Name: TOSHIBA MK1234GSX
  HDD Serial Number: XXXXXXXXX
  ATAPI Device: HL-DT-ST DVDRAM GMA-4082N
  System BIOS Version: V1.20
  VGA BIOS Version: nVidia 5.72.22.31.41
  KBC Version: V0.33
  UUID: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Main
  System Time: [XX:XX:XX]
  System Date: [XX/XX/XXXX]
  System Memory: 640 KB
  Extended Memory: 1002 MB
  Power on Display: [Auto]
  Language: [English (US)]
Advanced
  Internal Touchpad: [Enabled]
 
  Built-in LAN: [Enabled]
  Network Boot Protocol: [PXE]
 
  USB KB/Mouse/FDD Emulation: [Enabled]
 
  Wake on Keyboard: [Disabled]
 
  Thermal Mode Control: [Performance]
 
  Execute-Disable Bit Capability [Disabled]
 
  Core Multi-Processing: [Enabled]
 
Security
  Supervisor Password Is: Clear
  User Password Is: Clear
 
  Set Supervisor Password: [Enter]
  Set User Password: [Enter]
 
Boot
  +HDD
  CD/DVD
  FDD 
  LAN 
Exit
  Exit Saving Changes
  Exit Discarding Changes
  Load Setup Defaults 
  Discard Changes
  Save Changes
 

```
where would i disable the sound card from my bios? this option is not offered. i have my default set to conexant.

---

