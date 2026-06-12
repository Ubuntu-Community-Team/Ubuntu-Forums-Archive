---
title: "built in SD card reader not working."
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by liammoko on 2007-09-28
Running FF7.04 on Toshiba satelite p25-s607. Not many problems but SD reader is not working. Can sombody help. Be gentile I'm a newbie. ](*,)

---

### Post by Linux_Man on 2007-09-28
Could just be that there isn't a driver for it :( things like that happen mostly on laptops, try the 7.10 beta CD in live-cd mode to see if a driver got added for it, because laptop hardware is poorly documented, it usually doesn't have generic drivers for it. But try 7.10 beta in live-cd to see if its supported, then in October it will work :popcorn: and this is the easiest way unless you want to write a kernel driver, which we wouldn't mind but wouldn't be easy for a newbie :guitar:

---

### Post by wormser on 2007-09-28
We need to find out what model of card reader you have.  Post the results of the following code.  Applications> Accessories> Terminal

```
lspci
```

---

### Post by tipiglen on 2007-09-29
I have the same problem, but with a Fujitsu-siemens Amilo D

Code:
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator

Any suggestions welcome. 
Thanks in advance
ed

---

### Post by tipiglen on 2007-09-29
Meanwhile I've got a usb thingie which takes an SD card, and that works fine.  I understand the vendor of my built-in card reader is slow in providing linux drivers.....

I'd still like a driver for the slot.

salaam/Shalom/Shanthi/Dorood/Peace
ed

---

