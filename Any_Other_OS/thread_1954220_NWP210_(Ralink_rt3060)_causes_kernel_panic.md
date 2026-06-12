---
title: "NWP210 (Ralink rt3060) causes kernel panic"
date: 2012-04-07
forum: Any Other OS
---

### Post by phoenix1963 on 2012-04-07
Hi all, I'm afraid I'm using Mint 12, but see more relevant info over here...

I couldn't see my network out-of-the-box, so I installed the latest Ralink driver as in this thread [http://ubuntuforums.org/showthread.php?t=1608095]("http://ubuntuforums.org/showthread.php?t=1608095").

For reasons below, I reduced the debug printing as in this post [http://ubuntuforums.org/showthread.php?t=1702840]("http://http://ubuntuforums.org/showthread.php?t=1702840") .

Everything seemed to be working fine, until I tried large data downloads - then I get a kernel panic and the only messages I can find that might be remotely useful in syslog are ```

Apr  7 17:24:16 lbox dbus[539]: [system] Successfully activated service 'org.gno
me.SettingsDaemon.DateTimeMechanism'
Apr  7 17:24:51 lbox kernel: [   88.396530] ondemand governor failed, too long t
ransition latency of HW, fallback to performance governor
Apr  7 17:37:45 lbox kernel: imklog 5.8.1, log source = /proc/kmsg started.

``` 

you can see some message about ondemand governor before the next boot.

Any ideas gratefully received,

phoenix1963

---

### Post by Perfect Storm on 2012-04-07
Moved to Other OS/Distro Talk.

---

### Post by phoenix1963 on 2012-05-06
I never solved this problem - there seems to be an incompatability between the Ralink drivers and older hardware running this kernel.
I bought another wireless card with a chipset known to work (TP-Link TL-WN851N Wireless N PCI Adapter) and it runs flawlessly.

phoenix1963

---

