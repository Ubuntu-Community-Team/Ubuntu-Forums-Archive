---
title: "Firestarter not detecting active connection"
date: 2005-05-22
forum: Absolute Beginner Talk
---

### Post by Bendji on 2005-05-22
I've just installed Ubuntu a few days ago (my first linux distro) and needless to say, i'm a complete newb.  Anyway, one of the problems I'm having at this point is trying to get firestarter working.  I downloaded and installed as instructed by the unofficial guide.  My internet connection is obviously working, and the ethernet connection shows up as active under network settings.  But when i start firestarter i get an error saying that device eth0 is not ready.  
I've searched through the forums but i couldn't find a solution.  Any help would be greatly appreciated.  

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:D3:DC:85
          inet6 addr: fe80::20c:6eff:fed3:dc85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16232633 (15.4 MiB)  TX bytes:121216334 (115.6 MiB)
          Interrupt:22 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3482176 (3.3 MiB)  TX bytes:3482176 (3.3 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:156.34.41.141  P-t-P:142.166.182.4  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:15605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:5594617 (5.3 MiB)  TX bytes:18797907 (17.9 MiB)

I don't know if this info helps but as far as I can tell this is usually requested, thought I might as well include it.  Once again, I'm sorry if I'm not including enough (or the right) info.

---

### Post by wvslkr on 2005-05-22
Your ifconfig indicates you are using ppp0 for your connection rather than eth0.

I am not familiar with Firestarter, but a quick glance at their web page shows a 
wizard that you can run and change the setting.  Hope that helps. :)

---

### Post by Bendji on 2005-05-23
I didn't even realize that i was using ppp0.  I have much to learn......Anyway, firestarter's working now, thanks a lot for the help :)

---

