---
title: "winmodem driver"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Ins0mau on 2007-08-05
Hi guys,

I really like Ubuntu but it's really important for me to get it to connect to the net via my laptop's winmodem. I'm often at places that have no other internet access (most of the time actually).

I used Sisoft Sandra to get some info about my modem:

> Model SENS LT56ADW Modem
COM3


Device Information:

FUll Name: Agere SoftModem Version 2.1.51

NVRAM settings 1 2.1.51, AMR INtel MB, AC97 ID:SIL REV: 0x27,01


Is this information helpful? I've been doing a bit a google search but haven't been able to find a driver for it. I think Agere is related to Lucent modems??

Anyway, I know this question gets asked all the time. So I'm sorry to have to ask but I haven't been able to find info on my particular modem. Thanks heaps!

Dave


Update, I've used that scanmodem tool and it gave me this:

 > Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
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
 scanModem update of:  2007_August_01


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1e.3	8086:266d	144d:2115	Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 18:     448419   IO-APIC-fasteoi   ipw2200

 --- Bootup diagnostics for card in PCI slot 00:1e.3 ----
[   15.125807] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   15.125820] ACPI: PCI interrupt for device 0000:00:1e.3 disabled

 The PCI slot 00:1e.3 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

CodecFiles not found


 Intel Corporation 82801FB/FBM/FR/FW/FRW ??

That sounds different to what Sisoft Sandra told me in Windows... Now I'm REALLY confused. :s

---

### Post by ticklecricket on 2007-08-05
[www.linmodems.org](www.linmodems.org)

If it's not there you're pretty much hosed. Winmodems depend on windows to emulate basic modem functions. You could probably get a pcmcia or expresscard modem that isn't a winmodem.

---

### Post by Ins0mau on 2007-08-05
> **ticklecricket said:**
> [www.linmodems.org](www.linmodems.org)

If it's not there you're pretty much hosed. Winmodems depend on windows to emulate basic modem functions. You could probably get a pcmcia or expresscard modem that isn't a winmodem.

Yeah, I think I might have to do that.

Kind of a shock to realise your laptop's "modem" doesn't actually exist. In reality you just have a plug for a phone line for the raw analog signal to go in. The real "modem" is the software. Kind of feel ripped off.

---

### Post by bliffle on 2007-09-15
I'm trying to solve this problem for IBM thinkpads, T40 and 570, that have the Lucent Agere WinModem. After several days of following detailed and complex instructions and installing a couple hundred MB of code I couldn't get it working so I went to the computer store and bought a USB modem (Humingbird HUC56S with Conexant V.92: linux mentioned on box).

"scanModem" and "lsusb" detect both the Lucent and the Humingbird modems, but neither "gnome ppp" on ubuntu nor "kppp" on kubuntu detect either modem. Sometimes I really need dialup internet access, so this is a big problem. Luckily, I have Windows XP in a partition on the TP570 in a dual boot with kubuntu. That's what I'm using right now.  But this really limits my internet access, and endangers my whole move from XP to ubuntu.

I'll return the USB modem and exchange it for the PCMCIA version, but I'm not optimistic.

I also have problems getting a wireless adapter going for the 570, but that's another story.

---

