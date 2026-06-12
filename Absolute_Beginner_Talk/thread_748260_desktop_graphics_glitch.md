---
title: "desktop graphics glitch"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by awyea on 2008-04-07
my desktop and all programs that i try to run have vertical lines that run down it. they are always in the same spots, but they get worse as i type or move the mouse or change windows. i install xgl and disabled compiz and the lines are still there and it now bogs with everything. I have an goal3+ motherboard with integrated graphics. any help would be appreciated!!!

---

### Post by billgoldberg on 2008-04-07
> **awyea said:**
> my desktop and all programs that i try to run have vertical lines that run down it. they are always in the same spots, but they get worse as i type or move the mouse or change windows. i install xgl and disabled compiz and the lines are still there and it now bogs with everything. I have an goal3+ motherboard with integrated graphics. any help would be appreciated!!!

Try going to "system -> administration -> restricted drivers management" and look if you can install something.

---

### Post by smurphy_it on 2008-04-07
What type of video card do you have ?

Perhaps it is a driver issue, and needs a better driver.  Are you using the restricted drivers ?  Goto system, administration, restricted drivers manager and see if you can download the drivers for your video card.

Otherwise go into a terminal and post the output of the command

lspci

---

### Post by awyea on 2008-04-08
the video card is all integrated into the motherboard. the only restricted drivers i have are for my modem, which is currently not in use. here is the output.

tunes@tunes:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 IDE interface: Silicon Integrated Systems [SiS] Unknown device 0183 (rev 01)
00:0a.0 Communication controller: ESS Technology ES2898 Modem (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

---

### Post by helmut_hed on 2008-05-01
That actually sounds like bad video memory to me...  Any better luck under other OSes?

Regards,
Jeff

---

### Post by SeanHodges on 2008-05-01
I'm inclined to agree with helmut_hed, I had a similar problem years ago with an old S3virge graphics card - vertical lines along the screen that got increasingly worse the longer my computer was turned on. I also found that when switching to console mode (Ctrl-Alt-F1) and typing in commands, the characters on the screen would slowly become garbled.

Check if you are still getting this issue when running off the Ubuntu Live CD. If you are I'd hazard a guess that your integrated graphics chipset is nearing the end of its life and you'll need to buy a new graphics card.

If not, then you probably have a display configuration issue, but at least you'll know for sure.

Edit: theres a chance this could even be a system RAM problem, so don't rush out and buy a new graphics card without reporting back first...

---

