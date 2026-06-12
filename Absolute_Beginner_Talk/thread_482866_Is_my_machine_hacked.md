---
title: "Is my machine hacked?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by iluminate on 2007-06-24
Hello all,

I just did a process check on my machine and found this -
104       5488  0.0  0.1   1896   632 ?        S<s  Jun23   0:00 avahi-autoipd: [eth0] bound 169.254.7.92
root      5489  0.0  0.0   1684   284 ?        S<s  Jun23   0:00 avahi-autoipd: [eth0] callout dispatcher

Can someone let me know what this is?

Regards,
Lummi

---

### Post by shifty_powers on 2007-06-24
eth0 is your ethernet/lan connection. I'm guessing that you have a router for your internet connection, and that the i.p. address is yours.

```
ifconfig
```

See what that tells you ;)

---

### Post by iluminate on 2007-06-24
Ifconfig displayed -
The user who is using this computer is a moron =)

I actually did a trace on that IP and received a host in Germany?? But isn't this an internal IP?

Except for the moron message I got -

eth0      Link encap:Ethernet  HWaddr 00:0E:A6:C4:C9:1D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:C4:C3:C9  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fec4:c3c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:765500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:685533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:632556048 (603.2 MiB)  TX bytes:289717081 (276.2 MiB)
          Interrupt:19 

eth0:avah Link encap:Ethernet  HWaddr 00:0E:A6:C4:C9:1D  
          inet addr:169.254.7.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x6000 

All ok?

Cheers

---

### Post by shifty_powers on 2007-06-24
> **iluminate said:**
> Ifconfig displayed -
The user who is using this computer is a moron =)

I actually did a trace on that IP and received a host in Germany?? But isn't this an internal IP?

Except for the moron message I got -

eth0      Link encap:Ethernet  HWaddr 00:0E:A6:C4:C9:1D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:C4:C3:C9  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fec4:c3c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:765500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:685533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:632556048 (603.2 MiB)  TX bytes:289717081 (276.2 MiB)
          Interrupt:19 

[b][u]eth0:avah Link encap:Ethernet  HWaddr 00:0E:A6:C4:C9:1D  
          inet addr:169.254.7.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x6000[/u][/b] 

All ok?

Cheers

It was just your actual ip address. Remember that traces are far from perfect and that your ip traffic can go many various and wondeful places on its travels ;)

---

### Post by iluminate on 2007-06-24
Ok just installed tracerout on my local machine -

sudo apt-get install traceroute

And did the trace from my local host instead of using a web based trace..heh...
Now it traces to my local machine...sorry for being a n00b

Cheers m8s!

---

