---
title: "&quot;No root found&quot; after dual installing Max OSX and Ubuntu"
date: 2010-07-17
forum: Apple Hardware Users
---

### Post by clmcleod on 2010-07-17
Hello all,

Well I installed Ubuntu alongside my Mac OSX operating system and everything works great when booting Ubuntu. But when I go to boot Mac OSX it gives me a long list of data and finally stops at "FireWire initialized". After this it continues to say "still waiting on root". I've done some research and some believe that it has something to do with SATA drivers not being loaded, but I do not have my LeoV3 DVD and all of the other solutions I have tried have failed me. I did check the sticky about booting and it specifically says if you have dual booted then post your setup here. Thanks for any help, I'll answer any questions if you have them

EDIT: this is the end of what is showing up on my screen.

```

venderid: 0x8086 deviceid: 0x104b
FireWire (OHCI) Lucent ID 5811 PCI now active, GUID 00902700022a0e25;  max speed s400
Still waiting for root device

```

i think this is the answer to my question, but I don't know what it means. If someone could explain it that would be great.

> 
I had similar issues and it was due to my BIOS settings.  you need to  check these and make sure you have correct setup - Make sure that your  SATA mode is set to AHCI

This will give you some idea what you need to be looking at but it is  NOT specific to your board

   AHCI, SATA, or RAID controllers are available, set them to enabled
Speed Step is present, set to disabled
If EIST is present, set to disabled
HPET set to 64-Bit Mode
If you have an IDE controller, set to disabled
HDD S.M.A.R.T. Capability [Enabled]
CPU Enhanced Halt [Disabled]
CPU Thermal Monitor [Disabled]
CPU EIST Function [Disabled]
USB Keyboard Function [Enabled]
USB Mouse Function [Enabled]
SATA RAID/AHCI Mode [AHCI]
Onboard SATA/IDE Device [AHCI]
HPET Mode [64-bit Mode]


---

