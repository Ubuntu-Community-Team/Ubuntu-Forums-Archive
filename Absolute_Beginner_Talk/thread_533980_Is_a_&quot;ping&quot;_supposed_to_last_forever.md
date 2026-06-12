---
title: "Is a &quot;ping&quot; supposed to last forever?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by rexregum on 2007-08-24
I've tried pinging various IP addresses from MoBlock.

Each time, the terminal hangs indefinately.

How long does this normally take?

---

### Post by shof2k on 2007-08-24
> **rexregum said:**
> I've tried pinging various IP addresses from MoBlock.

Each time, the terminal hangs indefinately.

How long does this normally take?

PIngs should take less than a second to reply.  The ping command will keep pinging an ip until you press CTRL+C (Control key and the C key at the same time).

---

### Post by steve.horsley on 2007-08-24
ping will just keep sending pings at 1 second intervals until you stop it with Ctrl-C. You can limit the number of pings with ping -c <count> - see **man ping**,

---

### Post by Golyadkin on 2007-08-24
You can specify how many pings it should send, usually 10 is enough: 
>  ping -n 10 <ipaddress>

---

### Post by ank0ku on 2007-08-24
Now maybe I'm wrong about this, but isn't it possible to not receive a "pong" response? Maybe their ports are stealthed. Or the packet was lost somehow.

---

### Post by eentonig on 2007-08-24
> rfonteyn@gauloises:~$ ping tigra.local
PING tigra.local (192.168.1.9) 56(84) bytes of data.
64 bytes from tigra.local (192.168.1.9): icmp_seq=1 ttl=64 time=0.189 ms

--- tigra.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.189/0.189/0.189/0.000 ms
rfonteyn@gauloises:~$ ping -v tigra.local
PING tigra.local (192.168.1.9) 56(84) bytes of data.
64 bytes from tigra.local (192.168.1.9): icmp_seq=1 ttl=64 time=0.250 ms
64 bytes from tigra.local (192.168.1.9): icmp_seq=2 ttl=64 time=0.202 ms
64 bytes from tigra.local (192.168.1.9): icmp_seq=3 ttl=64 time=0.223 ms

--- tigra.local ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.202/0.225/0.250/0.019 ms
rfonteyn@gauloises:~$ 


As you can see. Just ping <hostname|ip-address> doesn't show any output untill you interrupt it.

If you supply the -v (verbose) parameter, you see the individual replies.

---

### Post by PilotJLR on 2007-08-24
> **ank0ku said:**
> Now maybe I'm wrong about this, but isn't it possible to not receive a "pong" response? Maybe their ports are stealthed. Or the packet was lost somehow.

Sure is. A lot of firewalls will silently drop ICMP packets, which prevents a ping response. Some people do call this "stealth mode."

---

### Post by Golyadkin on 2007-08-25
Many routers by default block ICMP ping replies.

---

