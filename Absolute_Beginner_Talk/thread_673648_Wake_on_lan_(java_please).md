---
title: "Wake on lan (java please)"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by skippy_1 on 2008-01-20
I'm trying to turn on wake on lan on my Ubuntu 7.10 system but the following command
sudo ethtool -s eth0 wol g
Even though I am a root user and supply the correct password it still says
"Cannot get current wake-on-lan settings: Operation not supported
  not setting wol"
Any advice?
I've already enabled it from the BIOS.

Also I can't find a 'safe' program to send magic packets **to** my Ubuntu machine **from** my smartphone. Any recommendations for a java thing?

---

### Post by blueridgedog on 2008-01-21
Are you certain that the hardware used on eth0 supports wake on LAN?  My read of the error is that it isn't.  Support in the BIOs is not equal to support on the Ethernet Chipset.

---

