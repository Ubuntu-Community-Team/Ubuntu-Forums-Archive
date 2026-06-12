---
title: "Firefox works, but no other net programs work!"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Andos on 2006-11-14
Hi all,

I'm new to linux, I just installed Dapper 6.06 on my machine to have a play, been stuck on windows for too many years now! Once I booted in, I got my wireless up and running but couldn't surf the web. After much swearing, and booting back into win XP, I disabled IPV6 in the blacklist in /etc/modprobe.d and firefox now works!  I'm posting from Ubuntu right now!

However, no other internet applications work!  GAIM won't sign into MSN, and apt-get just hangs when I run update as below:

> andy@andy-desktop:/etc/apt$ sudo apt-get update
0% [Connecting to gb.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.

My wireless card is an Asus Wi@home one, not sure on exact model but its based on RALINK RT2500 chipest below are the status reports.  Thanks for any help you can give!

> andy@andy-desktop:/etc/apt$ sudo iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"Tinternet"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:30:54:40:6D:7A
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr: off   Fragment thr: off
          Encryption key:1234-5654-32   Security mode: open
          Link Quality=84/100  Signal level=-59 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by Andos on 2006-11-14
Its ok I found a solution in the network forum, once i worked out what to search for ;) it was a problem with my router overwriting the DNS settings.

---

