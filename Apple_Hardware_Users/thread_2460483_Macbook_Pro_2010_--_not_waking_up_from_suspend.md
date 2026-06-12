---
title: "Macbook Pro 2010 -- not waking up from suspend"
date: 2021-04-11
forum: Apple Hardware Users
---

### Post by lukebart on 2021-04-11
Hey y'all,

Any solves or fixes for a Macbook Pro 2010 not waking up from suspend? I'm using Xubuntu 20.04. Everything else has been working great. Just can't figure out this one annoying issue, or if there is an actual solve. Been searching the internet for days for possible fixes.

---

### Post by CelticWarrior on 2021-04-11
Please post the hardware specifications, particularly the graphics.

---

### Post by lukebart on 2021-04-11
Hey CelticWarrior, thanks for responding. Here you go:

It's a Macbook Pro 7,1 - included some info below - it's a Geforce 320M. I'm using the Nouveau Graphics driver.

00:00.0 Host bridge: NVIDIA Corporation MCP89 HOST Bridge (rev a1)
00:00.1 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation Device 0d6d (rev a1)
00:01.1 RAM memory: NVIDIA Corporation Device 0d6e (rev a1)
00:01.2 RAM memory: NVIDIA Corporation Device 0d6f (rev a1)
00:01.3 RAM memory: NVIDIA Corporation Device 0d70 (rev a1)
00:02.0 RAM memory: NVIDIA Corporation Device 0d71 (rev a1)
00:02.1 RAM memory: NVIDIA Corporation Device 0d72 (rev a1)
00:03.0 ISA bridge: NVIDIA Corporation MCP89 LPC Bridge (rev a2)
00:03.1 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:03.2 SMBus: NVIDIA Corporation MCP89 SMBus (rev a1)
00:03.3 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:03.4 Co-processor: NVIDIA Corporation MCP89 Co-Processor (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:06.0 USB controller: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:06.1 USB controller: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:08.0 Audio device: NVIDIA Corporation MCP89 High Definition Audio (rev a2)
00:0a.0 SATA controller: NVIDIA Corporation MCP89 SATA Controller (AHCI mode) (rev a2)
00:0b.0 RAM memory: NVIDIA Corporation Device 0d75 (rev a1)
00:0e.0 PCI bridge: NVIDIA Corporation Device 0d9a (rev a1)
00:15.0 PCI bridge: NVIDIA Corporation Device 0d9b (rev a1)
00:16.0 PCI bridge: NVIDIA Corporation Device 0d9b (rev a1)
00:17.0 PCI bridge: NVIDIA Corporation MCP89 PCI Express Bridge (rev a1)
01:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 08)
02:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Inc. and subsidiaries NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
04:00.0 VGA compatible controller: NVIDIA Corporation MCP89 [GeForce 320M] (rev a2)



description: CPU
product: Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz
vendor: Intel Corp.
physical id:
0
bus info:
cpu@0
version: Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz
slot: U2E1
size: 1243MHz
capacity: 2400MHz
width: 64 bits
clock: 266MHz

---

### Post by CelticWarrior on 2021-04-12
> [COLOR=#000000]it's a Geforce 320M. I'm using the Nouveau Graphics driver.[/COLOR]
As expected.
In order to have suspension properly working you need the proprietary Nvidia driver 340. Not sure if still available for 20.04.

---

### Post by scorp123 on 2021-04-18
> **CelticWarrior said:**
> ...  you need the proprietary Nvidia driver 340. Not sure if still available for 20.04.

Why wouldn't it be? :-k

Me: running Ubuntu 20.04 on a 2009 "MacBook Pro 5,4" and the proprietary Nvidia graphics driver because this laptop has a Nvidia GeForce 9400M card. Just make sure you install the package version that's appropriate for the chip in the laptop.

Different story if you plan to run e.g. Mac OS on this super old MacBook ... that will not work unless you resort to methods that are very likely unfit for being discussed here. But free OS such as the many Linux or BSD variants will work tip top here.

---

### Post by CelticWarrior on 2021-04-18
> **scorp123 said:**
> Why wouldn't it be? :-k


Because it's older than Gordon Ramsay's mother's knickers? :biggrin:

---

### Post by scorp123 on 2021-04-19
> **CelticWarrior said:**
> Because it's older than Gordon Ramsay's mother's knickers? :biggrin:

But this is Linux ... and older hardware (even if it's from Apple) is usually much less of a problem and easier to get working than new models. I'd be much more worried about shiny new hardware, especially if it's from Apple. You see *"this (proprietary) piece of hardware is too new, no Linux support yet"* ](*,) much more often than *"this piece of hardware is too old and Linux won't run here anymore"*. In fact, with the exception of some distributions dropping support for 32-bit CPU's, I've never ever seen the latter. :-k

---

### Post by CelticWarrior on 2021-04-19
You're right, but my comment was regarding the Nvidia driver. Those get dropped, you know.

340 is LTS (Nvidia's) and still available but for how long?
One of the previous LTS branches, 304, needed for some still very capable cards doesn't compile with kernels newer that the first delivered with Ubuntu 16.04 and was therefore and henceforth removed. Sooner than later the same will happen to the 340 branch.

---

### Post by scorp123 on 2021-04-19
> **CelticWarrior said:**
>  340 is LTS (Nvidia's) and still available but for how long? One of the previous LTS branches, 304, needed for some still very capable cards doesn't compile with kernels newer that the first delivered with Ubuntu 16.04 and was therefore and henceforth removed. Sooner than later the same will happen to the 340 branch.

Yes, that's the bummer about proprietary stuff and depending on a specific vendor. Linus Torvalds' comment about Nvidia comes to mind ... :lolflag:

---

### Post by kencu on 2021-06-20
Something you might try... use the "Suspend" menu item first.

I'm running the 64bit version of Ubuntu 20.10 on a 2006 MacBook 2,1. <https://everymac.com/ultimate-mac-lookup/?search_keywords=MacBook2,1>.

Everything works just fine, but there is a problem when I close the lid to suspend. However, using the menu item works nicely, the systems suspends, then I close the lid. It all wakes up nicely when I open the lid next time.

Volunteering this in case it might work for you too.

---

