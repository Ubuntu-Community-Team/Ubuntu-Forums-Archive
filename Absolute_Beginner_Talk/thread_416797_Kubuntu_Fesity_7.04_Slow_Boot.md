---
title: "Kubuntu Fesity 7.04 Slow Boot"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by bubbalouie on 2007-04-21
Hi All,

This is my first post so apologies if anything is awry, I felt I have learned so much from these forums that I should try contribute something (although right now I have nothing significant).

I found that Feisty has a terrible boot time on my laptop compared to my server (roughly 3x as long) even though it is a faster computer. I have managed to bring my boot time from over a minute to roughly 30 seconds by doing the following:

```
sudo kate /etc/network/interfaces
```

Now comment out the wireless card (in this case *eth1*)

> 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[B]#auto eth1
#iface eth1 inet dhcp[/B]

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



The boot time has improved immensely, and my wireless still works fine (with WPA2) once KDE boots, I expect that mounting of network shares at boot may break if you use wireless though, right now I haven't verified this.

Cheers

Ryan

---

### Post by IgnacioMiller on 2007-04-21
Hey Ryan,

Welcome to the forum! Thanks for the tip, but I think it would be more widely read if you posted it in the[ tutorials and tips forum]("http://ubuntuforums.org/forumdisplay.php?f=100").

Thanks again!

---

### Post by bubbalouie on 2007-04-21
> **IgnacioMiller said:**
> Hey Ryan,

Welcome to the forum! Thanks for the tip, but I think it would be more widely read if you posted it in the[ tutorials and tips forum]("http://ubuntuforums.org/forumdisplay.php?f=100").

Thanks again!

Whoops My bad :confused:

---

