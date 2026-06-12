---
title: "Trouble with Linux finding Ethernet cards"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by dcoulshed on 2007-05-22
I'm trying to change an old office computer from Windows to Linux 6.06, and have tried both Debian and now Ubuntu.  I mainly want it to get access to the Internet.

The system is an AMD Athlon TX (whatever that is!) with 256 MB RAM, 30 GByte HD, and a Realtek 8139/810x Family PCI Ethernet NIC.  I'm using an i386 disto of Ubuntu now, downloaded onto CD (at work!).  

Trouble is Linux (neither distro) recognises the Realtek device.  It is built in to the motherboard, so I cannot change it.  I've tried Ubuntu 7.04 also and that doesn't allow recognition of the NIC either.  The rest of Linux appears to work OK, though I've no idea how to test this yet!

Debian gave the option of choosing a Realtek 8139 when it was installing and didn't autodetect the device, but still doesn't recognise that it is there.

What do I do next?

Thanks

---

### Post by wormser on 2007-05-22
I am not that good with hardware yet, but if you post the following commands to give us more information to work with.

```
lspci
```

In linux **ifconfig** is like ipconfig in windows.  Check to see if the adapter shows up.

---

### Post by dcoulshed on 2007-05-23
I accidentally set up a second thread (couoldn't see the first one and thought it was lost).  I've tried lspci, as it says:
.....  I've a Windows PC at home that keeps crashing, connected through a Speedtouch 510v4 Router and I want to put this one alongside and then convert entirely.  Can't get over the first hurdle of getting this one going, though.

I've tried to follow others' questions, but am stuck.  
In Terminal, typing "lspci" just takes me straight back to the command line (does that mean there's no PCI devices found?).  
Same for "lsusb".  
Typing "ifconfig" gives:

lo   Link encap:Local loopback
      inet addr: 127.0.0.1  Mask: 255.0.0.0
      inet addr:  : : 1/128  Scope: Host
      UP LOOPBACK RUNNING   MTU: 16436   Metric:1
      RX packets: 277 errors:0  dropped:0  overruns:0  frame:0
      TX packets: 277 errors:0  dropped:0  overruns:0  carrier:0
      collisions:0 txqueuelen:0
      RX bytes: 15328  (14.9 KiB)  TX Bytes: 15328  (14.9 KiB)

Where do I go from here?

Thanks

---

### Post by chemtut on 2007-05-23
this answer might seem a little odd ,but I had the same problemand solved it by having the computer connected to the router at boot!
I don't know why it worked,but it did!!!

good luck

---

