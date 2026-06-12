---
title: "Wifi disconnects with power plug"
date: 2012-05-15
forum: Apple Hardware Users
---

### Post by Tamalin on 2012-05-15
A rather interesting problem has arisen on my Ubuntu laptop (a Macbook).  When I remove the charging cable so the computer runs on battery, the internet stops working!  There is no "disconnected" message, but I can't ping any servers or see any webpages.  If I plug the cable back in, my internet works again, essentially instantaneously.

EDIT: Interesting note: It is only incoming packets that I'm not getting, apparently.  If I ping a computer, then unplug, I stop getting any returned packets, until I plug the power back in and I get a slew, as if they were "waiting at the door".

Does anyone know what is causing this issue, or maybe how to fix it?

I am running Ubuntu 12.04, but the same problem was present under 10.10.

---

### Post by Tamalin on 2012-05-22
Update:

IPv6 is disabled on both my router and laptop.
```

$ dmesg | grep eth1
eth1: no IPv6 router present
eth1: no IPv6 router present
eth1: no IPv6 router present
eth1: no IPv6 router present
eth1: no IPv6 router present
eth1: no IPv6 router present

$ cat /var/log/syslog | grep eth1
...
May 23 22:32:34 user-macbook NetworkManager[872]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 23 22:32:34 user-macbook NetworkManager[872]: <info> (eth1): deactivating device (reason 'none') [0]
May 23 22:32:34 user-macbook avahi-daemon[883]: Withdrawing address record for fe80::9227:e4ff:fefe:e36b on eth1.
May 23 22:32:34 user-macbook avahi-daemon[883]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::9227:e4ff:fefe:e36b.
May 23 22:32:34 user-macbook avahi-daemon[883]: Interface eth1.IPv6 no longer relevant for mDNS.
May 23 22:32:34 user-macbook NetworkManager[872]: <info> (eth1): supplicant interface state: completed -> disconnected
May 23 22:32:36 user-macbook avahi-daemon[883]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::9227:e4ff:fefe:e36b.
May 23 22:32:36 user-macbook avahi-daemon[883]: New relevant interface eth1.IPv6 for mDNS.
May 23 22:32:36 user-macbook avahi-daemon[883]: Registering new address record for fe80::9227:e4ff:fefe:e36b on eth1.*.

$ cat /proc/interrupts | grep eth1
 23:      32469          0   IO-APIC-fasteoi   eth1, snd_hda_intel

```

---

### Post by Tamalin on 2012-05-31
Ok, I got the wifi to connect by running:
```
$ sudo iwconfig eth1 power off
```

However, I have to redo this every time I turn on the computer or wake it up from sleep.  I tried adding "iwconfig eth1 power off" to /etc/rc.local, but it doesn't seem to resolve the issue.
What do I need to do?

---

