---
title: "Installed Ubuntu on LG Notebook no audio"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Paddatjie on 2007-06-03
Hi, I installed Ubuntu on my LG LW70 notebook, everything works fine. The only problem is that the sound is gone.

nat@nat:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:00.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:00.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:00.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by mohnkern on 2007-06-19
It's definitely seeing the audio:

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)


Is it possible that its just really really quiet?  That's what I'm seeing.

---

### Post by Everywhere_at_Once on 2008-01-27
It's a matter of creating a text file and telling the computer what kind of audio it should use.
I'll post back when i find the solution again. 

Just re-installed ubuntu on my LG lappy, and now i have to solve this for about the 7th time. Such a pain in the ***.

---

### Post by Theomack on 2008-02-05
I'm having the same problem.  I am just learning to use Ubuntu and this is the first challenge I've run into thus far.  From what I can see the sound card is recognized when I'm in the terminal but I don't have any sound.

---

