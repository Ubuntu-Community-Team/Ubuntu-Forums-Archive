---
title: "Wireless internet Static ip"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by libertas on 2008-04-07
im trying to convert my DHCP to a static address because azureus will not run properly on DHCP, i can figure out what my static ip i can figure out what the static ip and submask addresses are but i can't figure out what the gate way address is, ive used "ifconfig" in the command line and got this

 Link encap:Ethernet  HWaddr 00:19:7E:84:5E:40  
          inet addr:192.168.*.**  Bcast:192.168.*.***  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe84:5e40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:848954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1173098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:200944172 (191.6 MB)  TX bytes:956185999 (911.8 MB)
          Interrupt:17 Memory:54100000-54110000 

i used the "inet addr" as the static ip and the 255.255.255.0 as the mask, i do not know what the gateway address is or how to get it.

---

### Post by eriqjaffe on 2008-04-07
The gateway address should be the IP address of your router - probably 192.168.1.1 or 192.168.0.1.

---

### Post by Jest3r on 2008-04-07
$ netstat -nr

This will give you the gateway when it is already configured. A guess would be that the gateway would be a default. **192.168.0.1 **

---

### Post by MrFSL on 2008-04-08
also:
```
route | grep default
```
If it has already been configured by dhcp.

---

### Post by libertas on 2008-04-09
thanks guys :popcorn: when i typed in 'netstat -nr' i got a bunch of address and i search for the wireless internet and it had the gateway information for it, thankyou for all the help! :KS

---

