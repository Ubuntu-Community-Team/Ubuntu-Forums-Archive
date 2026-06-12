---
title: "Sound is extremely highpitched"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-22
When I play a sound through my speakers there is a very high pitched sound, but it's only when I play something does this sound occur.  what can I do to fix this

---

### Post by Dapman01 on 2007-10-22
Bump

---

### Post by Dapman01 on 2007-10-22
Noone? :(

---

### Post by Dapman01 on 2007-10-22
Another thing is, when I try to mess with the sound in the open volume control, I lose all sound until my next restart

---

### Post by cfaulkner on 2007-10-22
go into console and type

lspci


and also, post an attachment of what your dmesg says

or make an attachment of /var/log/messages

---

### Post by Dapman01 on 2007-10-22
This is onboard sound

---

### Post by Dapman01 on 2007-10-22
:guitar:

---

### Post by Dr Small on 2007-10-22
Please use [www.pastebin.com](www.pastebin.com) for long logs :|

---

### Post by Dapman01 on 2007-10-22
> **Dr Small said:**
> Please use [www.pastebin.com](www.pastebin.com) for long logs :|
[May I ask why]("http://pastebin.com/m7c45e5cf") (trying not to be rude)

---

### Post by Dapman01 on 2007-10-22
:confused:

---

### Post by cfaulkner on 2007-10-22
> **Dapman01 said:**
> This is onboard sound

still, post your lspci please

---

### Post by Dapman01 on 2007-10-22
patrick@patrick-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller

Hope it wasn't too long but there it is

---

### Post by Dapman01 on 2007-10-22
no one?

---

### Post by Dapman01 on 2007-10-22
bump

---

### Post by Dapman01 on 2007-10-22
Ok, I think that I am giving a lack of information, limme give you guys some info
Motherboard: Asus A8N-VM
OS: ubuntu 7.10
Oddity: High pitched screaming, only heard when playing some kind of sound.  when the volume is adjusted via ubuntu then all sound ceases.

ANY kind of help is greatly appreciated

---

