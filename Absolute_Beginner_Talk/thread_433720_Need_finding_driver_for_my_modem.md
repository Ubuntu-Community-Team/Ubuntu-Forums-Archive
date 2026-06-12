---
title: "Need finding driver for my modem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-05-05
I cannot get high speed internet at my location!! This is a linmodem for dial up use.
The mother board is made by Sybtax and it's a model S845GE. It uses Intel's 845G/845GE (GMCH) and 82801DB (ICH4) chipsets. I'm not sure if this is good or bad? Suppose to be AC'97 compliant.
I have 600mb ddr ram. 2.4ghz P4 processor and 160g hard drive
thanks

---

### Post by orange2k on 2007-05-05
What kind of modem do you have? Is it dial-up, ADSL (USB or ethernet) or something else?

---

### Post by Bachstelze on 2007-05-05
Please run a ScanModem scan on it and post the ModemData.txt file here.

[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

---

### Post by linuxjerk on 2007-05-06
Here is the modemdata.txt from scan modem.

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2007_March_15


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1f.6	8086:24c6	1019:0c04	Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
169:        609   IO-APIC-level  Intel 82801DB-ICH4

 --- Bootup diagnositcs for card in PCI slot 00:1f.6 ----
[17179570.880000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 169
[17179570.880000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

 The PCI slot 00:1f.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

ALSAversion 1.0.11
The audio card is not a modem hosting type.

---

### Post by oilchangeguy on 2007-05-06
the user has started several threads about getting a dial-up modem to work. if it's not going to work, there's no reason to keep creating new threads about it. just give up and get highspeed, or find a linux distro that will work with your modem. i've had good luck with xandros 3.0 oce. (no i don't use dial-up myself, why connect at maybe 50kps, when i can connect at over 4700kps. installed xandros on a friends computer)

---

### Post by helmut_hed on 2007-05-06
linuxjerk, have you tried the Smartlink (slmodem/slamr) driver for this modem?

8086:24c6 is supposed to be one of the supported PCI IDs, according to the source code.

Good luck,
Jeff
(I think I've replied to some of your other threads as well?)

---

### Post by linuxjerk on 2007-05-07
Thanks for your help... and yes I have started other threads, and got no replys or help that I knoiw of!!! 
 How do I get this forum to email me when there are replies to my threads?????????

I cannot get high speed. And you are right, I should be looking for a distro that works!

Ok I got sl-modem to install. When I run wvdial it won't send my username. Is there some delay
that I should be setting???
I know I have wvdial.conf set up right because it works with my other mother board which
has a pctel type modem.

---

