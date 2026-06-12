---
title: "Cannot access web pages at all"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Carlman on 2007-08-24
Hi all, 

Absolute noob here. 

When I boot Ubuntu, I get a message that "a wired conection has been established". 

However, when I open Firefox, I get an error message saying that it cannot access the server no matter what url I try. Firefox cannot open any web pages at all.

I have a cable connection wth dynamic IP address so I'm using the DHCP option. 

Do I need to configure Firefox or something? I'm outta ideas and I haven't found any other posts with my particular problem and/or setup. 

Suggestions?

---

### Post by wormser on 2007-08-24
It could just be a DNS issue.  Try putting 82.211.81.186 in the address bar in FireFox.  Here are a few other things to try.  Applications> Accessories> Terminal.

```
ifconfig
```

This is like ipconfig in a windows world.  You should see an IP address for you adapter.

```
ping ubuntuforums.org
```

```
ping 82.211.81.186
```

See if you can ping by url and IP address.  Post your results.

---

### Post by Carlman on 2007-08-25
(1) When I put 82.211.81.186 (or anything else) intot the FF address bar, I get:

"Firefox cannot establish a connection to the server at 82.211.81.186

- The site could be temporarily unavailable...
- If you are unable to load any pages at all, check your network connections.
- If your computer is protected by a firewall, make sure Firefox is permitted to access ther web..."      (no firewall)

(2) When I ping 82.211.81.186, I get:

"From 169.254.5.66 icmp_seq=1 Destination Host Unreachable"
"From 169.254.5.66 icmp_seq=2 Destination Host Unreachable"
"From 169.254.5.66 icmp_seq=3 Destination Host Unreachable"
etc.

Same thing when I ping ubuntuforums.org (or anything else).

(3) This is what I got with ifconfig in the terminal window:

eth0   Link encap: Ethernet HWaddr00:40:45:18:EF:17
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets: 282 errors:0 dropped:3386 overruns:0 frame:0
           collisions:0 txqueuelen:1000
           RX bytes: 17928 (17.5 KiB) TX bytes:3315 (3.2 KiB)

eth0:avah  Link encap: Ethernet HWaddr00:40:45:18:EF:17
          inet addr:169.254.5.66 Bcast: 169.254.255.255 Mask: 255.255.0.0
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          Interrupt:11 Base address: 0xd800

lo       Link encap: Local Loopback
         inet addr: 127.0.0.1  Mask 255.0.0.0 
        inet 6 addr: 1/128  Scope: Host
        UP LOOPBACK RUNNING MTU: 16436 Metric: 1
       RX packets: 66 errors: 0 dropped:0 overruns: 0 frame: 0
       TX packets: 66 errors: 0 dropped:0 overruns: 0 carrier: 0
       collisions: 0 txqueuelen:0
      RX bytes: 6200 TX bytes: 6200

---

