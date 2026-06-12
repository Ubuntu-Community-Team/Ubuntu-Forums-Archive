---
title: "Mac Desktop sleep issues"
date: 2005-04-18
forum: Apple PPC Users
---

### Post by spyguitar on 2005-04-18
I've seen lots of references to problems getting an iBook or Powerbook to sleep (and wake) correctly. Has anyone had trouble getting their PowerMac _desktop_ to sleep/wake? 

I'm running Hoary on a PowerMac G4 Silver with a 733 mHz processor. I can't seem to find any info on making my computer go to sleep. When I run 'apm' with no arguments, it tells me '32-bit APM interface not supported.'

---

### Post by callipeo on 2005-04-19
Could you provide more hardware info?

---

### Post by spyguitar on 2005-04-19
Sure:

Running Hoary official release, kernel 2.6.8.1-3-powerpc

PowerMac G4 733 mHz
1 GB RAM
80 GB Seagate HD (master - OS X)
40 GB Quantum HD (slave - Ubuntu)
Apple 15" LCD monitor 

cat /proc/apm returns:
0.5 1.1 0x00 0x00 0xff 0xff -1% -1 min

cat /proc/pci returns:
PCI devices found:
  Bus  0, device  11, function  0:
    Host bridge: Apple Computer Inc. UniNorth 1.5 AGP (rev 0).
      Master Capable.  Latency=16.
  Bus  0, device  16, function  0:
    VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev 161).
      IRQ 48.
      Master Capable.  Latency=248.  Min Gnt=5.Max Lat=1.
      Non-prefetchable 32 bit memory at 0x91000000 [0x91ffffff].
      Prefetchable 32 bit memory at 0x98000000 [0x9fffffff].
  Bus  1, device  11, function  0:
    Host bridge: Apple Computer Inc. UniNorth 1.5 PCI (rev 0).
      Master Capable.  Latency=16.
  Bus  1, device  23, function  0:
    Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 3).
      Master Capable.  Latency=16.
      Non-prefetchable 32 bit memory at 0x80000000 [0x8007ffff].
  Bus  1, device  24, function  0:
    USB Controller: Apple Computer Inc. KeyLargo USB (rev 0).
      IRQ 27.
      Master Capable.  Latency=16.  Min Gnt=3.Max Lat=86.
      Non-prefetchable 32 bit memory at 0x80081000 [0x80081fff].
  Bus  1, device  25, function  0:
    USB Controller: Apple Computer Inc. KeyLargo USB (#2) (rev 0).
      IRQ 28.
      Master Capable.  Latency=16.  Min Gnt=3.Max Lat=86.
      Non-prefetchable 32 bit memory at 0x80080000 [0x80080fff].
  Bus  2, device  11, function  0:
    Host bridge: Apple Computer Inc. UniNorth 1.5 Internal PCI (rev 0).
      Master Capable.  Latency=16.
  Bus  2, device  14, function  0:
    FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 0).
      IRQ 40.
      Master Capable.  Latency=16.  Min Gnt=12.Max Lat=24.
      Non-prefetchable 32 bit memory at 0xf5000000 [0xf5000fff].
  Bus  2, device  15, function  0:
    Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 1).
      IRQ 41.
      Master Capable.  Latency=16.  Min Gnt=64.Max Lat=64.
      Non-prefetchable 32 bit memory at 0xf5200000 [0xf53fffff].

I've also got a DVD burner and Zip 250 on my secondary IDE controller. Anything else you need?

---

### Post by callipeo on 2005-04-19
First of all, be warned that I'm new of apple hardware, so I may say some inaccuracy.

As far as I know, the biggest issue should be related to the nvidia graphic card. I don't know if pbbuttonsd would work for non-laptop machine (if so, you could type "pbbcmd QUERY SLEEPSUPPORTED" to get info), and I've heard some negative reports about sleep on ppc with nvidia card: however I found this thread on debian-powerpc:

[http://lists.debian.org/debian-powerpc/2004/02/msg00614.html](http://lists.debian.org/debian-powerpc/2004/02/msg00614.html)

and particularly this message:

[http://lists.debian.org/debian-powerpc/2004/02/msg00689.html](http://lists.debian.org/debian-powerpc/2004/02/msg00689.html)

I think the best thing you can do is try to install pmud and do some experiments.

---

