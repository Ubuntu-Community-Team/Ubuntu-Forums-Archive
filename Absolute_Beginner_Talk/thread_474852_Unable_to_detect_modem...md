---
title: "Unable to detect modem.."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-06-15
Hai everyone, I am a new user to ubuntu and I am unable to connect to the internet in ubuntu. I have a dialup 
connection and i do not know whether my modem is installed or not. I have a krypton HP56 modem and can someone give me the driver preferably in .deb. Can someone also give me a .deb package of vlc.....
Thanks in advance.


Rabindranath.

---

### Post by Bachstelze on 2007-06-15
This could be much more difficult than just installing a DEB... First of all, do a scanModem scan and post the ModemData.txt file here.

[http://132.68.73.235/linmodems/first.html](http://132.68.73.235/linmodems/first.html)

In short, what you have to do is :

1) Download scanModem : [http://132.68.73.235/linmodems/packages/scanModem.gz](http://132.68.73.235/linmodems/packages/scanModem.gz)

2) Copy it to your desktop in Ubuntu.

3) run the following commands :

```
cd
mv Desktop/scanModem.gz .
gunzip scanModem.gz
sudo ./scanModem

```

It will create a Modem directory with a bunch of text files in it. We need ModemData.txt.

---

### Post by Rabindranath on 2007-06-24
Here is the output from scan modem,


 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_June_19


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 06:01.0	134d:2189	134d:1002	Modem: PCTel Inc HSP56 MicroModem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 06:01.0 ----
[    3.297174] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ 20
[    3.297410] 0000:06:01.0: ttyS1 at I/O 0xb808 (irq = 20) is a 16450
[    3.297565] 0000:06:01.0: ttyS2 at I/O 0xb810 (irq = 20) is a 8250
[    3.297718] 0000:06:01.0: ttyS3 at I/O 0xb818 (irq = 20) is a 16450
[    3.297787] Couldn't register serial port 0000:06:01.0: -28

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:2668	8086:e202	Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 16:      69469          0   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, i915@pci:0000:00:02.0

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[   16.601981] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.602006] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:2668 is a High Definition Audio card, possibly hosting a soft modem.

---

