---
title: "Ubuntu 7.10 on HP 2510P"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by GuhnooYang on 2007-12-26
Hi all,


I cannot install Ubuntu 7.10 on HP 2510P! 


I can see the install welcome UI, but when i select the "install in text mode", the notebook down!


Why??!!

help me please!

---

### Post by RomeReactor on 2007-12-26
Hi. can you tell us more details about your laptop? CPU, memory, video card, etc.?

---

### Post by GuhnooYang on 2007-12-26
sure, as follows:



System features 
See detailed specs
 US QuickSpecs » html » pdf
 
Operating system
 Genuine Windows Vista® Business
Genuine Windows Vista® Home Basic
Genuine Windows® XP Professional
FreeDOS
 
Processors available
 Intel® Core™ 2 Duo ULV Processor U7600 (1.2 GHz, 533 MHz FSB, 2 MB L2 cache)
Intel® Core™ 2 Duo ULV Processor U7500 (1.06 GHz, 533 MHz FSB, 2 MB L2 cache)
 
Processor cache
 2 MB L2 cache
 
Chipset
 Mobile Intel® GM965
 
Client Management Solutions
 Intel Centrino Pro processor technology capable on select models
 
Memory 
Memory
 1 GB 667 MHz DDR2 SDRAM
2 GB 667 MHz DDR2 SDRAM
(Operates at a maximum of 533 MHz with 667 MHz memory)

 
Memory slots
 1 SODIMM slot
 
Storage 
Internal Storage
 60 GB 4200 rpm SMART PATA
80 GB 4200 rpm SMART PATA
64 GB Solid State Drive
(available October 2007)

 
Optical Drives
 DVD/CD Combo
DVD+/-RW SuperMulti with Double Layer
 
Audio, Slots, and Ports 
Audio
 High Definition Audio support w/24-bit DAC; Integrated mono speaker; Integrated microphone; Touch-sensitive controls for volume up, volume down, and mute; Stereo headphone/line out; Stereo microphone in
 
Ports
 Standard: 
2 USB 2.0
1 1394a
1 microphone in
1 headphone/line-out
1 RJ-11
1 external VGA monitor
1 AC power
1 docking connector
Rear: 
1 RJ-45

 
Slots
 1 Type I/II PC card
1 secure digital
(An optional Integrated Smart Card Reader is available and replaces the Type I/II PC card slot)

 
Graphics and Input/Output devices 
Display size
 12.1-inch diagonal Illumi-Lite, WXGA anti-glare
 
Graphics cards
 Mobile Intel Graphics Media Accelerator X3100, with up to 384 MB shared system memory
Microsoft DirectX 9 capable
 
Input devices
 Enhanced dual pointing devices: touchpad with scroll zone and pointstick, both with two pick buttons

 
Keyboard
 The 101/102-key compatible keyboard features an industry standard, full-pitch key layout with desktop keyboard features, such as the isolated inverted-T cursor control keys, editing keys, both left and right control and alt keys, and 12 function keys. US and International key layouts are available. Other features include an integrated numeric keypad, hotkeys for instant access to power conservation, brightness, and other features, 19-mm x 19-mm key pitch (center-to-center spacing), 2.5-mm stroke, comfort-dished keycaps, and bright key legends for improved visibility in low light conditions.

HP DuraKeys is a clear coating applied over the notebook keyboard that helps protect the finish and the printed characters on the keys. HP DuraFinish helps protect the finish on the keyboard deck, graphics, and icons from normal wear and tear.
 
Communication features 
Network
 Integrated Intel Gigabit Network Connection (10/100/1000 NIC)
 
Modem
 56K V.92 modem
 
Wireless
 Intel 802.11a/b/g draft n; Intel 802.11a/b/g; Broadcom 802.11a/b/g; Bluetooth 2.0
 
Broadband service provider
 AT&T Wireless BroadbandConnect; Verizon Wireless BroadbandAccess
 
Manageability 
Client Management Solutions
 Intel Centrino Pro processor technology capable on select models
 
Security management
 HP ProtectTools Security Manager; HP Fingerprint Sensor; Configuration Control Hardware; Memory Change Alert; Ownership Tag; Setup Password; Power-On Password; TPM 1.2 Embedded Security Chip (disabled where use is restricted by law); TPM Enhanced DriveLock (disabled where use is restricted by law); HP Disk Sanitizer; HP 3D DriveGuard; Kensington Lock Slot; Optional HP Privacy Filter
 
Compliance 
Approvals and Certifications
 ENERGY STAR® qualified
 
Product specifications 
Dimensions (w x d x h)
 11.11 x 8.38 x 0.97 in (282.30 x 212.80 x 24.70 mm)
 
Weight
 2.8 lb (1.29 kg)
 
Power and Battery 
Battery
 3-cell (28 WHr) high capacity Lithium-Ion; 6-cell (55 WHr) high capacity Lithium-Ion; 9-cell (83 WHr) high capacity Lithium-Ion
 
Power supply
 External 65-watt Smart AC adapter, 6-foot power cord included. Total length including external AC adapter is 12 feet. HP Fast Charge.
 
Service and Support 
Warranty - year(s)
 HP Services offers limited 3-year standard parts and labor warranty, pick-up or carry-in, and toll-free 7 x 24 hardware technical phone support; 1-year limited warranty on primary battery. On-site service and warranty upgrades are also available.

---

### Post by RomeReactor on 2007-12-26
By the specs you posted, I don't see anything that might interfere with the installer, except perhaps the wireless card; are you using the Live CD or the Alternate?

---

### Post by GuhnooYang on 2007-12-26
Alternate

---

### Post by RomeReactor on 2007-12-27
Is the Alternate CD 32-bit or 64? you may need to add boot parameters like **ACPI=OFF NOAPIC NOLAPIC**; try pressing F6--I think--at the "install in text mode" screen, before starting the installer. You should get a screen where you can command line add boot parameters, and I think also a list of them (sorry if this is not accurate; I haven't used the Alternate CD in a while).

---

### Post by CCNA_student on 2007-12-27
Try using the Live CD.

---

### Post by castrojo on 2007-12-27
I have a 2510p and hardy was the only thing that installed on it. I started this wiki page if you want to help fill it in:

[https://wiki.ubuntu.com/LaptopTestingTeam/HP2510p](https://wiki.ubuntu.com/LaptopTestingTeam/HP2510p)

With latest hardy and the 2.6.24 kernel the only thing that doesn't work for me is resume (it appears to suspend just fine, just not wake up).

---

### Post by RomeReactor on 2007-12-27
You may want to give CCNA_student's suggestion of using the Live CD a try; in case you still want to continue with the Alternate Cd, [these boot options]("https://help.ubuntu.com/community/Installation/32bitonAMD64") may help, though they may not be relevant for your system.

---

### Post by GuhnooYang on 2007-12-27
to RomeReactor,

"irqpoll pci=noacpi noapic nolapic acpi=off " don't work! :(

anyway, thanks all for your time!

---

### Post by blinxdk on 2007-12-27
It's certainly possible as I'm typing this from my 2510p with gutsy. Are there no error messages at all?

---

### Post by GuhnooYang on 2007-12-28
I cannot remember the error info, because it disappear soon.

but, i am sure that there is a string "error 71"

---

### Post by deragon on 2008-02-07
I confirm that I have the same problem with the Alternate CD of Hardy Heron 08.04 Alpha 4.  I never tried with any other version of Ubuntu.

The CD boots, but suddenly the screen goes blank (with the back light still on) and nothing happens, i.e. CDROM is not running anymore.  Caps lock and <ctrl>-<alt>-<del> do respond.  I cannot get to any of the consoles.

I tried Fedora Core 8, and the screen remains, but the installation stops after:

-----
running install...
running /sbin/loader
-----

Then nothing...

However, I did disable a bunch of devices in the BIOS, and the FC8 installation then worked.  Alas, that was not the case with 08.04 A4.

I am proceeding with the FC8 installation, to see if there are any other problem with it.  Of course, I have a preference for Ubuntu...

---

