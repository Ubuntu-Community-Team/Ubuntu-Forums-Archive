---
title: "Ubuntu 7.10 successfully installed atlast, but no audio coming"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by srinv9 on 2007-12-10
Hi,

  After so many attempts and re-installations due to Error 16 for the last time I again re-installed ubuntu 7.10 which I downloaded from the site. But all my attempts I noticed that I was not getting any audio. Mine is intel sound card and I checked lpsci and it is available. Appreciate if someone could help, I see that lot of people had this issue. My laptop is not that old only one and half year, and i wanted to try ubuntu from windows, so I removed windows xp totally, I already sense repentance unless someone help me with quick fixes.

thanks
Sri

---

### Post by Orivel on 2007-12-11
I had the same kind of problem and it was due to ALSA not supporting my sound card properly.  I installed OSS intead and it now works great. A guide to installing it can be found [here]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60")

---

### Post by srinv9 on 2007-12-11
> **Orivel said:**
> I had the same kind of problem and it was due to ALSA not supporting my sound card properly.  I installed OSS intead and it now works great. A guide to installing it can be found [here]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60")

  Thanks that worked like wonder, however the volume control is not working, I have to rely on my laptop volume buttons to increase the volume. Whenever I click that I get some gstreamer error something

---

### Post by srinv9 on 2007-12-11
Also if you have any prior experience as how to make youtube and other radio sites work, I installed the adobe flash plugin, but whenever I try to watch youtube, my laptop hangs and I have to force restart by toggling the blue button on my laptop :)

---

### Post by lvleph on 2007-12-11
There are massive amounts of post all about how to get Intel HDA sound working. Try searching for the version you have. The gstreamer error states something about not having a snd something or other device or maybe no codec, correct? (I can't remember the exact error) This could be the same issue that I dealt with. Figure out which sound card you have by typing
```
lspci
```
in a terminal. If you like, post it back here. BTW, always be wary of those that give advice, without knowing your specific setup.

---

### Post by Orivel on 2007-12-11
If you hold **Alt** and then press **F2** it will bring up the run application.  Then type **ossxmix**. This will bring up a GUI for adjusting the volume.

---

### Post by cold37 on 2007-12-12
i up date it to 7.10 i have no audio i try lspci and this is what i get--------------------------------------> 00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

