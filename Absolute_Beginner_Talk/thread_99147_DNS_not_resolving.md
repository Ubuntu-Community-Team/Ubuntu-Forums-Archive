---
title: "DNS not resolving"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by The Maste on 2005-12-05
I have found a lot of information on what may be the problem... the *problem* is that no other problem really fits what is going on with my machine.

Here is what occurs. I can not access a site by typing in google.com, ubuntuforums.org, etc. DNS simply doesn't resolve.

I can ping outside websites by their IP address.
I can access my router locally by typing in its address. (And change its configuration, etc)
I am recieving a valid IP address from my router through DHCP.

ifconfig results:
fei@Yggdrasil:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1B:B2:C5:99
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feb2:c599/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1885607 (1.7 MiB)  TX bytes:612825 (598.4 KiB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:57333 (55.9 KiB)  TX bytes:57333 (55.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::192.168.1.100/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:43 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I have an IP address bound to my machine.
The /etc/resolv.conf is pointing to the correct ip addresses given by comcast:
fei@Yggdrasil:/$ cat /etc/resolv.conf
search hsd1.ut.comcast.net.
nameserver 68.87.85.98
nameserver 68.87.69.146

More info:
fei@Yggdrasil:/$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

Router: LinkSys WRT54G

I *did* find a solution to the problem. But not one that I am satisfied with. The problem is resolved when I set DMZ to **enabled** and route it to the address bound to this pc (192.168.1.100).

Other fact: Internet works fine with Windows XP Professional. (Dual boot machine).

I figure it is time to ask those who have more experience than I do. I would appreciate any help. I know it is DNS, obviously. As to what exactly the router is doing to disallow ubuntu to resolve websites, I don't know. I'm sure it is something simple like making the router to resolve the sites by setting the nameserver to the router's domain gateway, instead of ubuntu. (That didn't work either, btw) Thank you. This has definitely been a learning experience.

---

### Post by timfrost on 2005-12-05
What happens when you issue command
  dig . ns @68.87.85.98
  dig . ns @68.87.69.146
in a terminal window?

You should get a list of root name servers, if those nameservers are responding to your DNS queries.

I get rejected, because they are not permitting DNS queries from outside:
tim@marvin:~$ dig . ns @68.87.69.146

; <<>> DiG 9.3.1 <<>> . ns @68.87.69.146
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 2384
;; flags: qr rd ra; QUERY: 0, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; Query time: 238 msec
;; SERVER: 68.87.69.146#53(68.87.69.146)
;; WHEN: Mon Dec  5 19:40:15 2005
;; MSG SIZE  rcvd: 12

which tells me that they are REFUSING my DNS query (which may be reasonable, since I am not one of their clients)
If they are refusing *your* DNS requests, then you need to get them to permit it from the routable address of your router (I assume that the router is doing NAT of your RFC1918 address to a valid address in your ISP network.

Other items to consider:
What is different about the DNS setup when you are booted into XP when compared to Ubuntu?  Can you force the DNS settings to match those on XP?
What firewall settings do you have on the PC (and the router)?
Some ADSL routers will do DNS proxying, but this requires configuration of the router.

---

### Post by The Maste on 2005-12-05
I get several lists of name servers using the dig command. But only when DMZ is enabled. When it is not enabled, it refuses saying:

fei@Yggdrasil:~$ dig . ns @68.87.69.146

; <<>> DiG 9.3.1 <<>> . ns @68.87.69.146
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached
fei@Yggdrasil:~$ dig . ns @68.87.69.146

; <<>> DiG 9.3.1 <<>> . ns @68.87.69.146
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached

It's very confusing. It seems like all I need to is open up the correct ports on my router to allow Ubuntu to access name servers. I have no idea which ports those are... or if that is even the problem.

As far as I know there is no difference between the addresses recieved from Windows XP to Ubuntu. They all look the same. The same name servers, IP Address, Gateway, etc.

I have no Firewall settings on the Ubuntu machine, but plan to once this is figured out. The Windows XP machine has only the Windows Firewall.

I was using Ubuntu 5.04 before last Saturday, and everything worked just fine. It was when I installed 5.10 that I started to have this problem.

Your help is appreciated. Thank you!

---

### Post by The Maste on 2005-12-05
I have no idea if the router is doing NAT of my RFC1918. As far as I can tell, from reading everywhere, it is.

There is a Firewall on the router. Something I forgot to mention. However, even if I disable the firewall it refuses to allow a connection if DMZ is disabled. It's not the router's firewall. It's such a wierd problem.

---

