---
title: "Networking/router problem in 6.10"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by hdunnigan on 2007-04-06
I have a dual boot machine (Vista and Ubuntu 6.10). The network card works fine in Vista (which was installed first) and seemed to work fine in Ubuntu (installed second). But now I am having problems. The *only* thing that changed in Ubuntu is that I edited the Grub so that Vista would still be an option, otherwise I have barely used Ubuntu.

Now, when I launch Ubuntu I cannot access the Internet.
Pinging the loopback works fine.
Pinging the router reports "network unavailable."

But the router works when running Vista, so I am confused.

Output from ifconfig is as follows (messy, sorry):

eth0      Link encap:Ethernet  HWaddr 00:19:DB:33:B6:FC          
inet6 addr: fe80::219:dbff:fe33:b6fc/64 
Scope:Link UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:230 errors:0 dropped:0 overruns:0 frame:0          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0         
collisions:0 txqueuelen:1000          
RX bytes:76636 (74.8 KiB)  TX bytes:0 (0.0 b)          
Interrupt:225 Base address:0xe000
lo        
Link encap:Local Loopback          
inet addr:127.0.0.1  Mask:255.0.0.1          
inet6 addr: ::1/128 Scope:Host         
UP LOOPBACK RUNNING  MTU:16436  Metric:1         
RX packets:163 errors:0 dropped:0 overruns:0 frame:0         
TX packets:163 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:0          
RX bytes:13544 (13.2 KiB)  
TX bytes:13544 (13.2 KiB)

Any thoughts on how to proceed?

---

### Post by steve.horsley on 2007-04-06
I see that eth0 doesn/t have an IP address. It needs one. Do you use DHCP or do you configure a static address? 

You can try this command to see of you get an address from DHCP :
**sudo dhclient eth0**

Also, have a rummage around the configuration utility you find in System->Administration->Networking. The settings you need to tweak should be in there. 

Three inportant things in the ifconfig output for eth0 you post:
* RUNNING means a cable is plugged in and it is working
* RX bytes in non-zero which confirms you are seeing packets from another machine
* TX bytes is 0 - you haven't sent any packets, not even a DHCP configuration request.

---

### Post by hdunnigan on 2007-04-06
Thanks for the quick response, I will try that as soon as I get home. :)

---

### Post by hdunnigan on 2007-04-06
I know it is good manners to report when a problem is fixed. Well, now I have connectivity restored, not sure why. Again, looking at what has changed, the problem went away when I unplugged my external hard drive. How that affects DHCP on my router I am unsure, but I am glad the networking is working again.

---

### Post by hdunnigan on 2007-04-13
Well, intermittent problems are never resolved. The problem that "solved itself" is back pretty much all the time again. I tried running

    sudo dhclient eth0

as was suggested. The Ubuntu machine failed to get a DHCP offer from the router. Boo. 

As I said in the initial post, this machine has no problem when booting into Vista, so I don't think it is a cabling problem or physical problem with the router.

Any other suggestions of what to try next? Thanks.

---

