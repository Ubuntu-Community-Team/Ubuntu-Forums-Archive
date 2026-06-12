---
title: "Why?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-14
Iv'e noticed that my threads arent really getting answered(My last thread keeps getting pushed down) The questions I ask are pretty straight foreward and I cannot understand why noone really replies. When someone replies its more half asked than anything. Usually directing me to a site that I dont understand. I want to make something clear. I am a real noob at computers and I just started learning. Please dont give me links and crap like that as they are usually beyond my understanding. I dont mean to impose or be a sore sucker, but its really annoying(Just check my wireless thread) Thank you for reading this and please go easy on me.

---

### Post by llamakc on 2007-11-14
I'll bite. I avoid threads (normally) that don't bother to be somewhat descriptive in the Title.

If you're looking to be hand-held you're going to probably have to pay for it, or learn to read for comprehension. Many of these things you find difficult now will be second nature very soon.

I recommend you try getting on IRC if you're looking for an immediate answer and don't have the skillset to utilize searching the forums or Google yet.

---

### Post by Dr Small on 2007-11-14
#ubuntuforums-beginners or #ubuntu will usually give you some quick support on irc.freenode.net

---

### Post by RobotoWorks on 2007-11-14
Im not Google dumb, but you guys areNoob blind, just because you all know a lot, doesnt mean that goes the same for others, can you tell me how to access IRC?

---

### Post by Inxsible on 2007-11-14
> **RobotoWorks said:**
> Iv'e noticed that my threads arent really getting answered(My last thread keeps getting pushed down) The questions I ask are pretty straight foreward and I cannot understand why noone really replies. When someone replies its more half asked than anything. Usually directing me to a site that I dont understand. I want to make something clear. I am a real noob at computers and I just started learning. Please dont give me links and crap like that as they are usually beyond my understanding. I dont mean to impose or be a sore sucker, but its really annoying(Just check my wireless thread) Thank you for reading this and please go easy on me.
I am sure no one is giving you links and crap. those link probably are related to the problem that you have.

if you dont give out enough information even after being asked (since you say ppl half ask you stuff) there is hardly anything, anyone can do for you.

---

### Post by Dr Small on 2007-11-14
> **RobotoWorks said:**
> Im not Google dumb, but you guys areNoob blind, just because you all know a lot, doesnt mean that goes the same for others, can you tell me how to access IRC?
Open a terminal, type:
```
sudo apt-get install xchat
```

Then launch Xchat.
Connect to FreeNode
Type:
```
/join #ubuntu
```
or
```
/join #ubuntuforums-beginners
```

---

### Post by RobotoWorks on 2007-11-14
I ment its half asked because the links are always confusing too me, as I said many of your replies go right over my head.

---

### Post by Dr Small on 2007-11-14
> **RobotoWorks said:**
> I ment its half asked because the links are always confusing too me, as I said many of your replies go right over my head.
My last reply went over your head ?

---

### Post by llamakc on 2007-11-14
> **RobotoWorks said:**
> I ment its half asked because the links are always confusing too me, as I said many of your replies go right over my head.

Then it is YOUR responsibility to voice that in the thread and ask for clarification.

---

### Post by Inxsible on 2007-11-14
Most importantly : People here are not paid to provide you with answers. They do it out of their own free will and its not like they are singling you out and not answering only your questions. 

if you be patient, they will get answered provided someone knows about it.

---

### Post by RobotoWorks on 2007-11-14
I have before, but people just keep giving me links or ask me a question I cant answer.

---

### Post by Inxsible on 2007-11-14
> **RobotoWorks said:**
> I have before, but people just keep giving me links or ask me a question I cant answer.Then you need to ask them to clarify. We do not know how proficient you are, but we will if you tell us.

anyway, this is going nowhere. Ask your problems and we shall help you sort them out as best as we can.

---

### Post by RobotoWorks on 2007-11-14
Thank you, would you be able to check out my Wireless problem thread, it should be on the second page

---

### Post by Paul820 on 2007-11-14
Usually links are posted because the information is there that somebody has already written, there is no point in us repeating that information again when it is already there for you to follow. If something goes over your head, ask the poster to explain what they mean, if you don't ask you don't get.

---

### Post by Dr Small on 2007-11-14
> **RobotoWorks said:**
> Thank you, would you be able to check out my Wireless problem thread, it should be on the second page
You mean here ?
[http://ubuntuforums.org/showthread.php?t=612496](http://ubuntuforums.org/showthread.php?t=612496)

---

### Post by llamakc on 2007-11-14
> **RobotoWorks said:**
> I have before, but people just keep giving me links or ask me a question I cant answer.

And again if you can not answer the question you have to be specific and say so.

For example, you've been asked at least twice in this thread to post the output of 'lspci'. So here we go again:

1. Open Gnome-Terminal by navigating to the menu and finding it via Applications | Accessories | Terminal 

2. Now that the terminal is opened type the following below. 

```

sudo lspci -v

```

3. ALL OF THE OUTPUT that is returned in the terminal, please cut/paste that BACK into this thread as a new post.

4. Do you know how to cut/paste from the terminal? Answer this question please.

---

### Post by RobotoWorks on 2007-11-14
Yes I do, and thanks thats the code Ive been looking for, heres what the terminal replied"

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d0300000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0400000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Memory at d0380000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0640000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: 0000000034000000-00000000340fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: d0100000-d01fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff10
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff10

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 20
        I/O ports at 2000 [size=256]
        Memory at d0000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 34000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

04:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at d0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

04:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0200800 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

04:06.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at d0200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

04:06.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0201000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

04:06.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at d0200900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

04:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at d0200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 3000 [size=128]
        Capabilities: [50] Power Management version 2

05:00.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Unknown device 18d7:0001
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at 38000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

05:00.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Unknown device 18d7:0001
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at 38001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

robotoworks@robotoworks-laptop:~$ 

Btw, what exact channel do I want to enter in IRC for help with my problem?

---

### Post by Dr Small on 2007-11-14
Either #ubuntu or #ubuntuforums-beginners, but #ubuntu is usually slam packed full and crowded.

---

