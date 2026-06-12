---
title: "Gutsy freezing -- possible solution factor"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by dansan on 2007-12-12
Hi all.

"Executive" summary: try dumping restricted Nvidia drivers. 

I have a newish Acer Aspire -- AMD Turion duo core processor, with 2GB RAM, etc. I'm a beginner with Ubuntu and not much of tech guy. At first, things went smoothly. I learned a lot from the Ubuntu support sites, and began getting Gnome into shape.

I also read complaints about Gutsy freezing. Then I began getting a taste of this, and my progress with Ubuntu froze, too. Within seconds of logging in, virtual cement. I started reversing changes I'd been making just before the Great Ubuntu Winter. :confused:

Unchecking the restricted Nvidia driver did it. Not so much eye candy now, but I can work and surf in peace.

If you've got Nvidia drivers and freezing, try this; you'll like it.

---

### Post by philinux on 2007-12-12
I assume you tried this site then?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by dansan on 2007-12-14
Hi Phil,

The resources you mentioned will be helpful. Thanks for pointing them out. I mean this despite what comes next.

I still haven't fully recovered my Gutsy installation after trying out Envy. Although it ran exactly as described, installing Nvidia drivers for me, the same freezing started immediately after I restarted. Naturally I went back to Envy to reverse what it did; it offers that option, but the result of choosing it was disastrous. I rebooted into black space, otherwise known as Terminal. I wasn't quite up to speed in that environment, so it took time (using Vista) to read the Ubuntu Forums. I can now boot into gdm or kde, but only in low-resolution mode (:().

So, I'll repeat my first post's recommendation. Nvidia sometimes just doesn't mix with Gutsy.

I booted off the Live CD and got normal resolution (1440 x 900), so I know it's possible. What my boot sequence reports is that my video card can't be properly detected, so the GUI starts in low-resolution. I have tried dpkg-reconfigure xserver-xorg from Terminal, but I must go wrong somewhere filling in the screens. No joy.

My next step, when time permits, will be to try xorg-edit.

---dan

---

### Post by hyper_ch on 2007-12-14
my nvidia card just runs fine on my computer. which one do you have?

> 
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)


---

### Post by dansan on 2007-12-15
Is this a clue to the driver problems? Here is what lspce -l returns:

> 00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)

---

### Post by philinux on 2007-12-15
Thats the sound card. Just post the output of

[FONT="Times New Roman"]lspci[/FONT]

---

### Post by Riffer on 2007-12-15
I had the same problem.  To fix it I did a complete reinstall (there were more then the video card problems that made this a must in my case) and then went and downloaded the new beta driver from the nVidia site (169.04 I think) installed those drivers.  

Everything now works well.

---

### Post by dansan on 2007-12-15
> **philinux said:**
> Thats the sound card. Just post the output of

[FONT="Times New Roman"]lspci[/FONT]

Whoops, wrong line pasted. Here's the entire out

> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
04:05.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
04:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by dansan on 2007-12-17
> **Riffer said:**
> I had the same problem.  To fix it I did a complete reinstall (there were more then the video card problems that made this a must in my case) and then went and downloaded the new beta driver from the nVidia site (169.04 I think) installed those drivers.  

Everything now works well.

Thanks for telling me this, Riffer. I may end up going the same route, but I'm tired of reinstalling every time somethings goes outa whack.

For a while, I thought I'd found the way. I re-ran Envy and got back normal resolution, but the freezing was also back. So I began uninstalling stuff, starting with kde. After returning to Gnome, the freezing was no longer instant as before, but after a fairish period of normal behavior, the big freeze was back. The only software remedy was the klutzy REISUB routine. By the way, freezing includes working not only in browsers like Firefox and Opera (tried both) but in terminal and file manager. The only time there was no freezing was while working in OpenOffice Writer and doing nothing on the desktop.

My final experiment last night was installing Xcfe and deactivating Gnome even though I knew there was little logic in doing so. The idea was to get as far away as possible from Firefox, which apparently underlies the other desktop environments. For all I know, Firefox also underlies Xcfe; anyway, Xubuntu freezes, too.

Maybe a Ubuntu guru will give me hint about further steps to take or confirm that reinstallation is the way to go.

dansan

---

