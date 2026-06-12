---
title: "drivers? modules? HELP!"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by commonslaughter on 2007-07-19
I am another completely new [ex- winXP] user, and I need help understanding and manipulating drivers and/or modules. 

I am on a new, clean install of 7.04, but I have zero drivers. How can I resolve this? Perhaps there's a wiki or something for rookies like me? What are the common protocols for locating and applying the software? I've got a brand new system, and Im dying to see what she's capable of doing. 

Thank you for your time.

---

### Post by Seisen on 2007-07-19
What drivers do you need? The more information you provide us the better.

---

### Post by commonslaughter on 2007-07-19
I ordered a Dell Intel Inspirion 530 and my read-out simply said it was an Intel "Integrated NIC card" . 

That's all of the information I have. I'm hoping Intel would make some pretty uniform linux network drivers. 

Im a totally new user, so what will I need to know for a successful install of the driver software?

Thanks in advance!

---

### Post by Seisen on 2007-07-19
Put this in the terminal and post it here. To access the terminal go to Applications>Accessories>terminal

```
lspci
```

---

### Post by musicarvind on 2007-07-19
> **Seisen said:**
> Put this in the terminal and post it here. To access the terminal go to Applications>Accessories>terminal

```
lspci
```

Hi Seisen,

well just like the OP of this thread, i am in the same position. ex-xp user. well mostly everything works fine.  everything seems to be auto install. learned how to install to hDD from a different forum.  I have one problem though. there is sound and the problem is that only one speaker is working. the other one is not. well anyways i have this information below and wondering how do i go about installing the right audio drivers. thanks a lot.

arvind@arvind-desktop:~$ lspci
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
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
arvind@arvind-desktop:~$

---

### Post by commonslaughter on 2007-07-20
Ok, I ran the command, and I got this:

amaad@amaad-mainframe:~$ lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 10c0 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0423 (rev a1)
amaad@amaad-mainframe:~$ 

It's very vague about the kind of ethernet controller, but the Dell is BRAND NEW, so I hope this isn't a big problem. Dell's support website lists for windows drivers. 

Thanks in advance.

---

### Post by gizmoarena on 2007-07-20
if you just want to know what is driver/modules. check [http://learningdevicedrivers.blogspot.com](http://learningdevicedrivers.blogspot.com) out.

---

### Post by Seisen on 2007-07-20
What is the exact model name of your Dell?

---

### Post by commonslaughter on 2007-07-20
Dell Inspirion 530. 

its the intel chipset, with a dual core processor.

---

### Post by Seisen on 2007-07-20
I haven't been able to find anything that will help but you might be better off posting you question here or asking a mod to move it their.

[http://ubuntuforums.org/forumdisplay.php?f=256]("http://ubuntuforums.org/forumdisplay.php?f=256")

---

