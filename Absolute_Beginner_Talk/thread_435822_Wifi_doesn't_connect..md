---
title: "Wifi doesn't connect."
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Voyager7777 on 2007-05-07
I have installed Ubuntu 7.04 on my Toshiba laptop. Everything seems to work and I 'm now trying to get wifi working with the US robotics 5410 pcmcia card.
The wifi card works and I can see several wireless networks, including my own. But when I try to connect I don't get a proper connection or an ip adress. I have tried with network manager and wifi radar, both with the same result.
The system works fine under xp.
I have turned off al safety measures on my router for testing, but in the end it is supposed to work with WPA-PSK security.
Advise is welcome.

---

### Post by silent1643 on 2007-05-07
check the last wiki post on this[ link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsUsRobotics")

---

### Post by Bachstelze on 2007-05-07
Have you tried using the good ol' command line to connect ?

```
sudo iwconfig ethX essid YOUR_ESSID
sudo dhclient ethX
```

Assuming your router runs DHCP. Of course, replace ethX with your interface name.

---

### Post by Voyager7777 on 2007-05-07
> **HymnToLife said:**
> Have you tried using the good ol' command line to connect ?

```
sudo iwconfig ethX essid YOUR_ESSID
sudo dhclient ethX
```

Assuming your router runs DHCP. Of course, replace ethX with your interface name.

Wow, thanks, that one worked.  (replacing ethX with wlanX)

Any way to get it working via network manager or wifi radar.

And now on to wpa....

---

