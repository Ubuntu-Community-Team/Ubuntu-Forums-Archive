---
title: "add packages with no internet"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Unni Kartha on 2007-06-05
no need to say myself a newbie to linux (started learning last week)

I have installed Ubuntu 7.04 at my home pc. i dont have an internet connection there...mainly because my modem is not working. Can anyone tell me how to dowload the packages from my office and install it in my home PC? I have a USB flash drive.

I followed the instructions in the ubuntu help page and this is the modemdata.txt file. what to do next?

----------------------------------------------------------------------------------------------------------------------------------
 
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
 scanModem update of:  2007_May_11
 

ALSAversion 1.0.13
USB modem not detected by lsusb
 
Modem or host audio card candidates have firmware information:
 
 PCI slot PCI ID  SubsystemID Name
 ---------- --------- --------- --------------
 06:00.0 1057:3052 1057:3020 Modem: Motorola Unknown device 3052 
 
 Modem interrupt assignment and sharing: 
 
 --- Bootup diagnositcs for card in PCI slot 06:00.0 ----
[    3.140409] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 21 (level, low) -> IRQ 20
[    3.140700] 0000:06:00.0: ttyS1 at I/O 0xb808 (irq = 20) is a 16450
[    3.140875] 0000:06:00.0: ttyS2 at I/O 0xb810 (irq = 20) is a 8250
[    3.141051] 0000:06:00.0: ttyS3 at I/O 0xb818 (irq = 20) is a 16450
[    3.141125] Couldn't register serial port 0000:06:00.0: -28
 
 PCI slot PCI ID  SubsystemID Name
 ---------- --------- --------- --------------
 00:1b.0 8086:2668 8086:e203 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 
 
 Modem interrupt assignment and sharing: 
 16:      31460          0   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, i915@pci:0000:00:02.0
 
 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[   18.203694] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.203718] PCI: Setting latency timer of device 0000:00:1b.0 to 64
 
 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===
 
8086:2668 is a High Definition Audio card, possibly hosting a soft modem.

----------------------------------------------------------------------------------------------------------------------------------

---

### Post by renzokuken on 2007-06-05
all the packages in the repos are available at archive.ununtu.com

downlaod the correct .deb file for you architecture (i386, amd64 etc) then transfer them to your ubuntu box and run

```
sudo dpkg -i name_of_file.deb
```

to install them

beware of dependencies though, you will have to take care of them yourself, without apt-get it is not done automtaically

---

