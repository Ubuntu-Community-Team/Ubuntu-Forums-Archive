---
title: "DNS problem?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by dileepk on 2006-11-28
I just installed desktop 6.0.6 version on dual core desktop.  I can ping some sites (yahoo, google) but can't ping some other (hp).   Also, I can't go to google from web browser but i can type ip address and that works.  My DNS shows its connected to router gateway.   Any ideas??

---

### Post by mssever on 2006-11-28
> **dileepk said:**
> I just installed desktop 6.0.6 version on dual core desktop.  I can ping some sites (yahoo, google) but can't ping some other (hp).   Also, I can't go to google from web browser but i can type ip address and that works.  My DNS shows its connected to router gateway.   Any ideas??

You might try using OpenDNS. Their DNS servers are: 208.67.222.222 and 208.67.220.220.

Failing that, can you ping your router or access the router config page? What happens if you connect directly to the Internet, bypassing the router?

---

### Post by ciscosurfer on 2006-11-28
If you can ping yahoo or google by name, then you probably don't have a DNS issue as your requests are being translated.

Try to also ping your router and that's probably a good jumping off point.

Can you also describe your problem in a little more detail please :-)

Please post the output of ```
ifconfig
cat /etc/hosts
cat /etc/resolv.conf
```

---

### Post by apral on 2006-11-28
I had a similar problem & the only solution for me was to manually enter the dns & static IP address of my ISP.A freindly phone call was all it took to find that out.Best of luck!:)

---

### Post by squidward_tentacels on 2006-11-28
Also, a entering "whois YOUR_ISP_HERE.com" from a terminal will normally list the DNS servers

---

### Post by dileepk on 2006-11-28
I tried adding open DNS - 208.67.222.222 and 208.67.220.220  but that has not solved the problem.   

Here is the output of 
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0E:0C:72:C9:E8
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fe72:c9e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10
          RX bytes:144982 (141.5 KiB)  TX bytes:11389 (11.1 KiB)
          Base address:0x2000 Memory:d0100000-d0120000

dileep@dileep-laptop:~$ cat /etc/resolv.conf
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.65
nameserver 208.67.222.222
nameserver 208.67.220.220
dileep@dileep-laptop:~$


These are additional DNS servers I added.   My ISP won't give me static address.   Btw, other laptops on the same system work fine (these are XP laptops).

Any further thoughts or ideas -- i am still stumped...

---

### Post by dileepk on 2006-11-28
Thanks everyone.  I filtered ipv6 from firefox and it now works fine.  i used about:config in the firefox address line and toggled ipv6.

in case someone else is having the same problem.

---

