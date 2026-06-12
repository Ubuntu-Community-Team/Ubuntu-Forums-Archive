---
title: "WiFi 811b Card won't stay active..."
date: 2006-03-12
forum: Apple PPC Users
---

### Post by mcoyle on 2006-03-12
Hello Gang,

I haven't run linux is a few years, still I feel I'm fairly experienced. I just installed 5.10 on a 17" Al-Powerbook.

I have a Lucent WiFi PC Card that I just can't get to stay active. The Wifi Manager can see my access point and the signal is strong. The card is NOT dhcp, but I'm pretty confident IP, gateway, etc. are all correct.

ONCE I got the card to work. Since then it fails only a few seconds after trying to active it.

Something that seems to have change in recent linux distros is the contents of the /etc/network folder. While the 'interfaces' file looks familar, the if-config files seem depreciated.

Anyone have a suggestion?

Edited: 03-16-06

It seems the problem the crappy Kcontrol Panel for Networking. Editing the /etc/network/interface file did the trick.


Thanks,
Michael

---

