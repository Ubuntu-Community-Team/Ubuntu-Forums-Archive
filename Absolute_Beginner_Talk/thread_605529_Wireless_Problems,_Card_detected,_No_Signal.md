---
title: "Wireless Problems, Card detected, No Signal"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by LobbyDizzle on 2007-11-07
Ok here's there dealio....

I have an HP dv2000nr with an AMD64. My wireless card is 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

I tried so many different things. I am a noob of course, keep that in mind. 

I tried blacklisting the original driver and using the bcm43xx driver, which seems to work(Wireless Connections is an option under Network Connections), but when I attempt to scan it does not work, look:

jared@jared-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jared@jared-laptop:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : No such device

I tried to connect to my router but it just keeps popping up asking for my WEP.

---

### Post by Griffiss on 2007-11-07
Have you tried wieman's excellent howto?

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by LobbyDizzle on 2007-11-07
That is just a tutorial on wireless security...

---

### Post by Griffiss on 2007-11-09
WEP is a form of wireless security. wieman's how to shows how to configure a network which uses it.

---

### Post by brons2 on 2007-11-09
Even Windows sysadmins know that WEP is totally worthless.  I won't degrade my wireless network into WEP just so that Ubuntu can participate.

---

### Post by Griffiss on 2007-11-09
Yes it is. the same howto also shows how to configure networks to use WPA.

---

