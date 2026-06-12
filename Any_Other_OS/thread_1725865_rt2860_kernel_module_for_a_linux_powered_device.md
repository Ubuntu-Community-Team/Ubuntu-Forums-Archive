---
title: "rt2860 kernel module for a linux powered device"
date: 2011-04-10
forum: Any Other OS
---

### Post by cherva on 2011-04-10
I have a linux powered satellite receiver (DreamBox 800) and I'm trying to get two wireless usb cards to work with it... the problem is that there are no drivers for rt2860 chipsets. Can someone help me find and modprobe the right kernel module for it ? Or can anyone point me to a nice tutorial about cross processor compiling so I can download the soure of kernel 2.6.18 and the rt2860 driver and compile the module for the dreambox.
 
Here is some more info on the device:
```
root@dm800:~# uname -a
Linux dm800 2.6.18-7.3-dm800 #1 Tue Apr 27 20:55:13 CEST 2010 7401c0 GNU/Linux
```

```
root@dm800:~# cat /proc/cpuinfo
system type             : BCM97xxx Settop Platform
build target            : dm800
processor               : 0
cpu model               : Brcm3300 V0.0
cpu MHz                 : 294.91
BogoMIPS                : 294.91    ( udelay_val : 147456  HZ = 1000 )
wait instruction        : yes
microsecond timers      : yes
tlb_entries             : 32
extra interrupt vector  : yes
hardware watchpoint     : no
ASEs implemented        : mips16
VCED exceptions         : not available
VCEI exceptions         : not available
RAC setting             : I/D-RAC enabled
unaligned access        : 3
rdhwr/brdhwr traps      : 0 / 0

```
Thanks for the help.

---

