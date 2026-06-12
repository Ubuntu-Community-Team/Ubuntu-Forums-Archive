---
title: "I CAN ping google BUT CAN'T browse!?"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by kxty on 2006-04-01
I just installed my Ubuntu recently, everything is fine except the internet. I'm using router connecting to a hub and share internet with 2 computers. I can access internet when I'm using Windows XP, but when I use Ubuntu I can't open any page with Firefox. I mean all the settings are good. Ethernet card is detected and actived, set to DHCP. And when I ping [www.google.com](www.google.com) with Networking Tool, I got replied. And I can access my router (10.1.1.1) with firefox.
/etc/resolv.conf contains:
nameserver 10.1.1.1

In the Networking Tool window, I can select Ethernet and my IP is set to 10.1.1.2

But when I type any URL like [www.google.com](www.google.com) in Firefox, I got nothing but a error after a long time says that can't open [www.google.com....](www.google.com....)](*,) 
Anyone can help me with this?

---

### Post by Zelut on 2006-04-01
It sounds like it might be a DNS issue.  You might want to log into your router & see if you can find the DNS address.  After you find that try adding that to the Networking Tool DNS Tab.

Let me know..

---

### Post by professor_chaos on 2006-04-01
kuyaedz is right, do what he says.

---

### Post by kxty on 2006-04-01
I found the DNS server address. and added it to System->Administration->Networking->DNS. Still can't access internet... And I ping [www.google.com](www.google.com) again, Packets transmitted: 5  Packets received: 5, Packagets loss: 0%.
Open [www.google.com](www.google.com) in firefox, after a long time, get an alert: The operation timed out when attempting to contact [www.google.com](www.google.com)

---

### Post by kxty on 2006-04-01
when ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0D:61:35:69:EB
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20d:61ff:fe35:69eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:53369 (52.1 KiB)  TX bytes:44978 (43.9 KiB)
          Base address:0x9000 Memory:fa000000-fa020000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:170095 (166.1 KiB)  TX bytes:170095 (166.1 KiB)

---

### Post by halitech on 2006-04-01
check here and see if it helps

[http://ubuntuforums.org/showthread.php?t=153138&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=153138&highlight=ipv6")

---

### Post by kxty on 2006-04-01
[QUOTE=halitech]check here and see if it helps

[http://ubuntuforums.org/showthread.php?t=153138&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=153138&highlight=ipv6")[/QUOTE]

WOW! GREAT! Thanks a lot man! It works now!!!
CHEERS!

---

### Post by halitech on 2006-04-01
welcome mate, didn't see it as a DNS issue cause you said you could ping google.com and if the DNS wasn't working, it wouldn't resolve the IP. took a shot at it being something about IPv6, something that didn't seem to affect me when I installed a few weeks back.

---

