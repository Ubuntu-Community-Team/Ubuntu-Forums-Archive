---
title: "Stuck in bios"
date: 2014-01-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by thedumbasd on 2014-01-03
Hi. I cleaned my hard drive in command prompt and now I'm stuck in bios. Can't really do anything, not even boot my windows DVD. Asked this on another forum, but nobody was able to help. Hopefully you guys can come up with something. Thank you

this is what I have in my bios

Aptio Setup Utility - Copyright ( C ) 2012 American Megatrends, Inc.


Main


BIOS Information
BIOS Vendor: American Megatrends
Version: 225
GOP Version: 3.0.14.2015
EC Version: 225


Processor Information: Intel ( R ) Core ( TM ) i7-360QM CPU @ 2.40 GHz


Memory Information
Total Memory: 8192 MB ( DDR3 )


System Information
Serial Number: CCN0CJ492339503


System Date
System Time


Access Level: Administrator


Advanced


Start Easy Flash
Internal Pointing Device: [ Enabled ]
Wake on Lid Open: [ Enabled ]
Power Off Energy Saving: [ Enabled ]


Intel Virtualization Technology: [ Enabled ]
Intel AES-NI: [ Enabled ]
VT-d: [Enabled]
> SATA Configuration
> Graphics Configuration
> Intel ( R ) Anti-Theft Technology Configuration
> USB Configuration
> Network Stack


Boot


Boot Configuration
Fast Boot: [ Disabled ]
Launch CSM: [ Enabled ]
Launch PXE OpROM: [ Enabled ]


Boot Option Priorities
Boot Option #1: P2: Slimtype DVD A DS8A9SH
Boot Option #2: P0: ST000LM024 HN-M101MBB
Boot Option #3: UEFI: IP4 Realtek Ethernet Controller
Boot Option #4: UEFI: IP6 Realtek Ethernet Controller
Boot Option #5: Realtek PXE B02 D00


Hard Drive BBS Priorities
CD/DVD ROM Drive BBS Priorities
Network Device BBS Priorities
Delete Boot Option


Security


If ONLY the Administrator's password is set, this only access to Setup and is only asked for when entering Setup.
If ONLY the User's password is set, this is a power on password and must be entered to boot to enter Setup.
In Setup the User will have Administrator rights.


Administrator Password Status: NOT INSTALLED
user password Status: NOT INSTALLED
Administrator Password
User Password


HDD User Password Status: NOT INSTALLED
Set Master Password
Set User Password


> I/O Interface Security


System Mode state: User
Secure Boot state: Disabled


Secure Boot Control: [ Disable ]


Save & Exit


Save Changes and Exit
Discard Changes and Exit


Save Options
Save Changes
Discard Changes


Restore Defaults


Boot override
UEFI: IP6 Realtek Ethernet Controller
UEFI: IP4 Realtek Ethernet Controller
P0: ST1000LM024 HN-M101MBB
P2: Slimtype DVD A DS8A9SH
Realtek PXE B02 D00


Launch EFT Shell from filesystem device


Also I get this, when I'm trying to boot the DVD


Intel UNDI, PXE-2.1 (build 083)
Copyright (C) 1997-2000 Intel Corporation


This Product is covered by one or more of the following patents:
US5, 307, 459, US5, 434, 872, US5, 732, 094, US6, 570, 884, US6, 115, 776 and US6, 327, 625


Realtek PCIe GBE Family Controller Series v2.41 (06/08/11)
PXE-E61: Media test failure, check cable


PXE-M0F: Exiting PXE ROM.


Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key_

---

### Post by E_Sound on 2014-01-04
What are you trying to do? First boot is device is DVD drive, so your BIOS settings seems to be OK. Except "Boot override" option, where "P2: Slimtype DVD A DS8A9SH" should be selected in the first position (if what's possible).
Make sure that your DVD image is bootable (if you are going to install windows) and press ESCAPE button while BIOS is loading (can be other button, it depends on BIOS).

---

### Post by thedumbasd on 2014-01-04
> **E_Sound said:**
> What are you trying to do? First boot is device is DVD drive, so your BIOS settings seems to be OK. Except "Boot override" option, where "P2: Slimtype DVD A DS8A9SH" should be selected in the first position (if what's possible).
Make sure that your DVD image is bootable (if you are going to install windows) and press ESCAPE button while BIOS is loading (can be other button, it depends on BIOS).

Thanks for the reply, looks like my DVD isn't bootable. Trying another one

---

### Post by mörgæs on 2014-01-05
Are you trying to install Buntu? If so then it's safer to use a USB stick.

---

