---
title: "eeepc 1001PG wired LAN constantly changing MAC address"
date: 2011-09-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by monsterfurby on 2011-09-27
I am using Ubuntu 11.04 on an Asus EeePC 1001PG running the newest BIOS and with all automatic updates currently installed. The Atheros card issue was thankfully fixed with one of the newer patches, but another issue has appeared now which is becoming rather irritating.

I am currently on a university network which requires users to register their devices by MAC address. However, when I entered my wired LAN connection's MAC, it was unable to recognize it. I managed to get it entered another way, but after rebooting the computer, I noticed that the hardware MAC for my ethernet card had changed. I restarted a few more times, with the MAC changing time and time again.

Finally, through several modifications (i.e. in                            /etc/network/interfaces amongst others), I got the system to at least occasionally bring up the MAC address I have registered to use the network, allowing me to go online.

The fun doesn't last very long, though, as after several minutes online (does not seem to be tied to traffic amount or activity), the connection collapses. It does not disconnect, it just no longer transfers any data. Upon disconnecting and reconnecting, there is one of three possible outcomes:

1. it reconnects with the working MAC
2. it takes a long time to reconnect, then gives me the 802.1x identification window with the options to cancel or connect (which then just re-opens the window), without anything else
3. it reconnects with a different MAC, forcing me to reboot the system as this MAC remains

The network uses 802.1x with PEAP, no certificate but only user name and password, and MSCHAP v2. 

I am completely lost here, but would greatly appreciate any hint or pointer towards how to solve this issue and possibly get a stable connection working once again.

Thanks a lot in advance!

---

