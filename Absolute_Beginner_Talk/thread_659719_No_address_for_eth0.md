---
title: "No address for eth0"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by ksujason on 2008-01-06
I just finished an installation of Umbuntu and am now trying to configure for internet access. I cant connect and also cant ping any address.
Following is the results from ifconfig. It looks like I dont have an address for eth0.

jason@jason-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:DB:E5:42:16   
          inet6 addr: fe80::219:dbff:fee5:4216/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1363 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:36612 (35.7 KB)  TX bytes:107449 (104.9 KB) 
          Interrupt:23 Base address:0xdc00  

Any thoughts on how to get an address would be appreciated.

Thanks

---

### Post by jordanmthomas on 2008-01-06
If you're using dhcp to get an IP, just do this:
```
sudo dhclient eth0
``` and you'll get an IP

edit
It looks like you've already got an IP though (albeit an ipv6 one)
If you're having connectivity problems, try looking up how to disable ipv6 and some of your troubles will likely go away.

---

