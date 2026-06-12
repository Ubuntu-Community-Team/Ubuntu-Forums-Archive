---
title: "Front Panel Audio / Onboard Sound"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-12-06
I am having trouble getting anything to output to my frontpanel headphone jack on the front of my system. It has to be plugged in correctly, as I just tested the mic jack beside it, and it worked perfectly, and this case audio jumper connection is bundled together, so there can be no messing it up when plugging it in.

I have no idea what kind of onboard sound card I have, so I can't give that information.
I do believe it is 8 channel though.

I am in gmix, and the below screenshot shows which settings control the audio through my speakers (plugged in at the back). All the others are muted. If anyone can assist me to get my front panel audio working, I would be more than pleased and thankful :)

Sincerely,
Dr Small

---

### Post by Dr Small on 2007-12-06
Also, from suggestion of st33med:
```
drsmall@darkghost:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

---

### Post by go_beep_yourself on 2007-12-09
I'm having the same problem, sound works, but mic doesnt with the same sound card.

---

### Post by vhaarr on 2008-03-11
Did you find a solution to this problem?

I'm having the exact same issue myself.

---

### Post by Dr Small on 2008-03-11
> **vhaarr said:**
> Did you find a solution to this problem?

I'm having the exact same issue myself.
No, sorry. No solution as of yet.
I did run a patch cord from the back of my speaker output jack from the I/O on my motheboard which comes out from under the desk and the speakers plug into it. When I want to use headphones, I unplug the speakers from the patch cord and plug in my headphones.

Not exactly a fix of how I wanted it, but it works. :|

Dr Small

---

