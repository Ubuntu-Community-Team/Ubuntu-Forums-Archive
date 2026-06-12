---
title: "nividia graphics card - black screen"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Marianne_S on 2008-01-31
last time i tried installing the nvidia graphics card (it was with 7.04) my screen went black and the log in wouldn't load. what can i do to avoid that now (i use 7.10 now)?



please ask if  you need hardware info to help me (sorry  i suck at stuff like that)

---

### Post by taurus on 2008-01-31
What nvidia card do you have?

---

### Post by dannyboy79 on 2008-01-31
please post the output of the following command entered into a termianl session (terminal can be found at Programs>Asseccories>Terminal

lspci

then paste the output here. thanks I can help from there

---

### Post by Marianne_S on 2008-01-31
dannyboy79: 

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
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
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)


taurus: does the above pasted text show which card i have?

---

### Post by taurus on 2008-01-31
> **Marianne_S said:**
> dannyboy79: 

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
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
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
**[COLOR="Blue"]02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)[/COLOR]**


taurus: does the above pasted text show which card i have?

System -> Administration -> Restricted Drivers Manager should have a driver for your card.

Otherwise, you can install the nvidia-glx-new.

---

### Post by Marianne_S on 2008-01-31
> **taurus said:**
> System -> Administration -> Restricted Drivers Manager should have a driver for your card.

Otherwise, you can install the nvidia-glx-new.

uh this is very typically of me - last time when my screen went black - what i did was installing the driver from restricted drivers manager  sorry sorry sorry... *blush*

---

### Post by pedro_orange on 2008-01-31
Ever tried using Envy? It sorts out everything for you, while you go and make yourself a cuppa.

---

### Post by Marianne_S on 2008-01-31
i am new to all of this  - i switched to linux cos i wanted to learn more about computers - so here it goes: 

what is envy ? how does it sort "everything out" and how do i use it/get it?

---

### Post by PmDematagoda on 2008-01-31
Envy is an application that you can use to install the Nvidia or ATi driver, the driver files are downloaded directly from the source, so the Nvidia driver comes directly from the Nvidia web site.

Envy can be obtained from [here]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by Marianne_S on 2008-01-31
and using envy will then avoid the whole screen going black? kinda scared to try without being 100% positivly sure

---

### Post by PmDematagoda on 2008-01-31
You cannot be very sure, sometimes even Envy can cause a black screen, but do not worry, just because you lose the GUI does not mean that you cannot fix the problem:).

---

### Post by Marianne_S on 2008-01-31
haha ok - i will try (after taking tons of backup)- thanks all of you for helping! 

and for the sake of learning - if anyone has time for this - does anyone know why the screen went black the first time i tried installing the driver? It is not super importaint for me to know - but it is nice to understand why too.

thanks once again :D

---

### Post by Marianne_S on 2008-01-31
envy worked! no black screen - 

compiz fusion is installed too and working nicely :D

 thanks so much!

---

