---
title: "[SOLVED] Nvidia GeForce 1600 for ubuntu 7.04"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by vegetosayajin on 2007-10-08
I have a problem with my Nvidia GeForce 1600 driver
and the problem is that I can't find a way to install it safely,the last time I install it from the updates when the sistem said that everithing is ok and I need to reboot,after the reboot there was only non-editable kernel dialog that I don't understand.And I had to install the whole sistem all over again:(
P.S.I am a complete   beginner at the whole linux sistem and I am using Dualboot sistem
Windows XP and Ubuntu 7.04 feisty fawn  (I think:-s)the problem with me is that I want to have etleast 1024/768 resolution but the current settings are only limited to 800/600



so how do I fix this problem(I'm a full beginner remember](*,))

---

### Post by overdrank on 2007-10-08
> **vegetosayajin said:**
> I have a problem with my Nvidia GeForce 1600 driver
and the problem is that I can't find a way to install it safely,the last time I install it from the updates when the sistem said that everithing is ok and I need to reboot,after the reboot there was only non-editable kernel dialog that I don't understand.
P.S.I am a complete   beginner at the whole linux sistem and I am using Dualboot sistem
Windows XP and Ubuntu 7.04 feisty fawn  (I think:-s)the problem with me is that I want to have etleast 1024/768 resolution but the current settings are only limited to 800/600



so how do I fix this problem(I'm a full beginner remember](*,))

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by vegetosayajin on 2007-10-08
> ivo@ivo-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
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
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
ivo@ivo-desktop:~$ 

there you go thanks for the fast response :)

---

### Post by overdrank on 2007-10-08
> **vegetosayajin said:**
> there you go thanks for the fast response :)
Ok this is your graphics card
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
Have you enabled the restricted drivers located under system, administration.

---

### Post by vegetosayajin on 2007-10-08
> **overdrank said:**
> Ok this is your graphics card
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
Have you enabled the restricted drivers located under system, administration.
Yes I have(the last time I enabled them when I restarted there was this problem I said earlier)
from where I can download this driver,sorry for the trouble,I am afraid to restart

---

### Post by overdrank on 2007-10-08
> **vegetosayajin said:**
> Yes I have(the last time I enabled them when I restarted there was this problem I said earlier)
from where I can download this driver,sorry for the trouble,I am afraid to restart

You can try Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by vegetosayajin on 2007-10-08
> **overdrank said:**
> You can try Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
thanks I'll reboot now and if you don't see me within 5-6 min. it doesn't work :lolflag:



Edit:[COLOR="Red"][SIZE="5"]It's perfect thanks dude I now am going to the Linux world[/SIZE][/COLOR]

---

### Post by overdrank on 2007-10-08
> **vegetosayajin said:**
> thanks I'll reboot now and if you don't see me within 5-6 min. it doesn't work :lolflag:



Edit:[COLOR="Red"][SIZE="5"]It's perfect thanks dude I now am going to the Linux world[/SIZE][/COLOR]

Great glad to here could mark the thread as solved under thread tools. Thanks and good luck! :guitar:

---

