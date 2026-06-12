---
title: "ubuntu-7.04-desktop-amd64.iso -&gt; hard hang on boot"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by AlanJo on 2007-05-03
Hello all,

First problem:
I downloaded and burnt ubuntu-7.04-desktop-amd64.iso to disk, but when I boot from the CD it hangs. 

I get the initial splash screen and can select "verify the CD" (or what ever the menu is called) and that reports the CD is good. 

When I try to then boot it, it hangs just after switching from the point where the orange rectangle bounces side to side to the point where it becomes a progress bar. I am unable to even switch to tty1  (Ctrl-Alt-F1, which should show boot status, not so?).

When it hits this state, it also stops responding to NumLock / CapsLock / ScrollLock. Totally locked.

Second problem:
The x64 ISO doesn't boot under Virtual PC. The x32 ISO does, but it doesn't seem to detect the virtualized mouse, so I am basicly stuck at that point. I can switch to the login prompt on tty1, but what I remember of command line Linux is from a *long* time ago in place far far away.

Regards,
Alan

--------------------------------
More details about my computer  (from Vista x64 RTM build).
 

Component Details Subscore Base score 
Processor Intel(R) Core(TM)2 CPU 6600 @ 2.40GHz 5.3 5.3 
  Determined by lowest subscore 
 
Memory (RAM) 4.00 GB 5.5 
Graphics Radeon X1950 Pro 5.9 
Gaming graphics 2047 MB Total available graphics memory 5.8 
Primary hard disk 89GB Free (194GB Total) 5.4 
Windows Vista (TM) Ultimate 

System   
--------------------------------------------------------------------------------
 
  Manufacturer System manufacturer 
  Model System Product Name 
  Total amount of system memory 4.00 GB RAM 
  System type 64-bit operating system 
  Number of processor cores 2 
 
Storage   
--------------------------------------------------------------------------------
 
  Total size of hard disk(s) 204 GB 
  Disk partition (C:) 89 GB Free (194 GB Total) 
  Disk partition (D:) 6 GB Free (10 GB Total) 
  Media drive (E:) CD/DVD 
 
Graphics   
--------------------------------------------------------------------------------
 
  Display adapter type Radeon X1950 Pro 
  Total available graphics memory 2047 MB 
        Dedicated graphics memory 256 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1791 MB 
  Display adapter driver version 8.351.0.0 
  Primary monitor resolution 1680x1050 
  DirectX version DirectX 9.0 or better 
 
Network   
--------------------------------------------------------------------------------
 
  Network Adapter Realtek RTL8168/8111 Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
  Network Adapter Microsoft Tun Miniport Adapter 
  Network Adapter NETGEAR 108 Mbps Wireless PCI Adapter WG311T 
  Network Adapter Virtual Machine Network Services Driver 
  Network Adapter Virtual Machine Network Services Driver

---

### Post by igknighted on 2007-05-03
Try hitting F6 at the boot screen before you select it to boot, then erasing the boot options "quiet" and "splash" so you see everything scroll by.  Whatever it freezes on if probably your issue.

---

### Post by HornedBeast on 2007-05-03
I found I needed to add the NOAPIC option to the end of my boot options.

When you get the options of what do to, press "F6". Scroll to the end where it says "quiet splash --" and change it to "queit splash noapic --"

This fixed my issues. Seemed to be something to do with my Dual Core CPU.

Hope it helps.

---

### Post by AlanJo on 2007-05-05
OK, more info:
With splash off, the last message it spewed was from pci_hotpug:__crc_cpci_hp_register_bus

See attached screen shot for the full description.

Next step is to try the noapic option.

---

### Post by AlanJo on 2007-05-05
Nope, still busted. With noapic it hangs about just after the "agppart: ... " line in the screen shot.

---

