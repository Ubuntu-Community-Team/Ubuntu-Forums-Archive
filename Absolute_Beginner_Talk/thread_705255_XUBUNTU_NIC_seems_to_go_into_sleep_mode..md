---
title: "XUBUNTU: NIC seems to go into sleep mode."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2008-02-23
Hi all,
I run @ home an old HP laserjet vectra, which I use as a fileserver, running Xubuntu.
Today i fitted in a new network card, because the onboard was so slow that copying a cd through the network would take me almost two hours.
I manage to connect allright and mount the shared folders, but after a moment of inactivity the other computers can no longer connect because (appearantly) the NIC goes into some sort of sleep mode. I had this problem as well when I had ubuntu running on this computer and was using the onboard NIC. I don't know how to turn this option off in Xubuntu (and I can't even remember how I did it in Ubuntu).
I tried turning off the screensaver, but that didn't help. I also used the slider to change the time b4 the computer is considered idle, but that didn't work either.
Can anybody help me? 
I don't know which of these two is the network card I am using know, but this is the lspci:

```
00:0b.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by julian67 on 2008-02-25
If you dual boot with Windows, or previously ran Windows, and it's the realtek card that is being used then there is a known issue. An update to the realtek 8139 Windows driver (and some other realteks I believe) reconfigured the cards so that the  "wake on lan after shutdown" feature became disabled. If you dual boot then it's easy enough to boot into Windows and either re-enable this feature or roll back the driver update. Please see [http://ubuntuforums.org/showthread.php?t=538448]("http://ubuntuforums.org/showthread.php?t=538448") for a fuller explanation and other possible solutions/workarounds.

---

