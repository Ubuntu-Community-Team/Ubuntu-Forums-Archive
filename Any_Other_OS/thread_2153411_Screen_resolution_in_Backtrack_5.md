---
title: "Screen resolution in Backtrack 5"
date: 2013-06-11
forum: Any Other OS
---

### Post by Slinkyfingers08 on 2013-06-11
I have an "MSi FX720 Laptop" and I am trying to enchance my resolution  in backtrack5 r3. So far I can only get 1024x768  (4:3) and 800x600  (4:3) and it will not recognize my monitor. I am wanting the system to  use my nvidia graphics. I have tried, time and time again, from  different tutorials, and the end results become a "no screen" error when  trying to log back into "startx" afterward. I am never able to recover  from the error (as I am still learning) so I have to reinstall. I am  running dual boot Backtrack 5 r3 alongside Windows 7 Professional. 
GETTING FRUSTRATED!! PLEASE HELP!!!

This is a fresh install and I know I may have to update to the latest version, as I have done numerous times before, but 
here is my system information:


MSi FX720 Notebook/Laptop

root@bt:~# lsb_release -a
No LSB modules are available. Distributor ID:    Ubuntu Description:    Ubuntu 10.04.3 LTS Release:    10.04 Codename:    lucid
 
root@bt:~# lspci -nn | grep -i 

vga  00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd  Generation Core Processor Family Integrated Graphics Controller  [8086:0116] (rev 09) 01:00.0 VGA compatible controller [0300]: nVidia  Corporation Device [10de:0df7] (rev a1)

root@bt:~# lshw -C display

*-display               
       
description: VGA compatible controller
       
product: nVidia Corporation
       
vendor: nVidia Corporation
       
physical id: 0
       
bus info: pci@0000:01:00.0
       
version: a1
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress bus_master cap_list rom
       
configuration: driver=nouveau latency=0
       
resources: irq:16 
memory:f6000000-f6ffffff 
memory:e0000000-efffffff 
memory:f0000000-f1ffffff 
ioport:e000(size=128) 
memory:f7000000-f707ffff
  
*-display UNCLAIMED
       
description: VGA compatible controller
       
product: 2nd Generation Core Processor Family Integrated Graphics Controller
       
vendor: Intel Corporation
       
physical id: 2
       
bus info: pci@0000:00:02.0
       
version: 09
       
width: 64 bits
       
clock: 33MHz
       
capabilities: msi pm bus_master cap_list
       
configuration: latency=0
       
resources: 
memory:f7400000-f77fffff 
memory:d0000000-dfffffff 
ioport:f000(size=64)

Thanks for your time! Hopefully some one can help me resolve this issue....

**QUICKLY RUNNING OUT OF COFFEE, SUGAR, AND PATIENCE**

---

### Post by lisati on 2013-06-11
Thread renamed and moved.

Your [other thread]("http://ubuntuforums.org/showthread.php?t=2153403"), which has been closed because of edits, had replies. It's getting confusing, not just because of the edits, but because of the multiple threads.

---

### Post by Cheesemill on 2013-06-11
Try using [Kali Linux]("http://www.kali.org/") instead of BackTrack as it has much better support for newer hardware.

---

