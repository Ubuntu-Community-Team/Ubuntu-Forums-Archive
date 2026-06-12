---
title: "Gutsy on P4 HT freezes"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by aryasudhanshu on 2008-04-01
Hi

I have Gutsy on my P4 HT box with nVidia 7600 GS graphics card. The system freezes randomly and becomes unresponsive every once in a while. If I leave it be for a while it comes back.

I have Compiz Fusion running smoothly so I guess the problem is not due to the graphics driver. There is no pattern in the freezes and no central application triggering them. They are very very frustrating and being a newbie to linux are very discouraging.

Please help me out.

Thanking in anticipation.

---

### Post by GuitarRocker2562 on 2008-04-01
I have a similar setup and no problems. What are your full specs? Is this a custom PC? If not, what model is it?

---

### Post by aryasudhanshu on 2008-04-02
Yeah its a custom PC. My specs are

~ P4 HT 3.0 GHz
~ nVidia 7600 GS
~ Intel D101 board
~ 768MB DDR RAM
~ 20GB PATA (with Gutsy)
~ 160GB SATA (NTFS with Windows XP)

Could the problem be of the kernel instead of hardware?

---

### Post by Crafty Kisses on 2008-04-02
Sounds like a resource issue, but your specs are pretty decent, post the following output:
```
top
```

---

### Post by aryasudhanshu on 2008-04-02
Here's what lspci gave me

[COLOR="RoyalBlue"]00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)[/COLOR]

---

### Post by aryasudhanshu on 2008-04-02
Result of top


top - 03:24:05 up 50 min,  3 users,  load average: 0.60, 0.56, 0.40
Tasks: 119 total,   1 running, 118 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.8%us,  0.8%sy,  0.0%ni, 91.2%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:    774464k total,   751376k used,    23088k free,   153532k buffers
Swap:   875500k total,    34708k used,   840792k free,   193420k cached

  PID   USER        PR   NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5392 sudhansh  15   0  177m  63m  19m S    9  8.4   3:21.39 rhythmbox          
 5358 sudhansh  15   0  121m 105m  17m S    1 14.0   1:19.66 Xgl                
 5128 root          15   0 27020  16m 4492 S    0  2.2   0:04.15 Xorg               
 5405 sudhansh  15   0 24348  18m 7444 S    0  2.4   0:08.03 compiz.real        
 6460 sudhansh  15   0 80320  19m  11m S    0  2.5   0:00.72 gnome-terminal     
    1 root      18   0  2952 1852  532 S    0  0.2   0:01.37 init               
    2 root      14  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.03 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      10  -5     0    0    0 S    0  0.0   0:00.07 kblockd/0

---

### Post by aryasudhanshu on 2008-04-16
Somebody please help me...
These freezes are freaking me out.

---

### Post by prshah on 2008-04-16
> **aryasudhanshu said:**
> Somebody please help me...
These freezes are freaking me out.

Just a suggestion; use the "memtest" option (Select from your grub menu at startup), let it run for 15~20 mins. Anything RED is bad.

---

