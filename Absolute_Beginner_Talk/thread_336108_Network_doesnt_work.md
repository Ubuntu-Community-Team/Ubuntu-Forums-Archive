---
title: "Network doesnt work"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by gojto on 2007-01-11
Hi. im new to linux and i heve installed ubuntu 6.10. i have a problem with my network. it seems it doesnt recognize  have a network card (wired) on my via p4pb motherboard because when i go to networking... there is only a modem connection that i can configure and nothing else. what shoud i do?

thx
Gojto

---

### Post by kidders on 2007-01-11
Hi there,

The first thing to try is to make sure Ubuntu even recognises your network adapter. **lspci** is like "ls" for your PCI bus. Here's what happens when I ask about mine...```
# lspci|grep -i eth
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

With luck, yours is recognised too. Next, see if you can identify whether Ubuntu has loaded a kernel module for it. Marvell adapters tend to use drivers with "sk" in the name, so I can check for...```
# lsmod |grep sk
skge                   38800  0 
```
You'll have to look up what driver your card should be using. If Ubuntu hasn't loaded the right driver for you, you can force it to ... I would do **sudo modprobe skge** on mine. All being well, you should be able to do this...```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 0A:11:D8:5A:BB:E0  
          inet addr:192.168.7.114  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::201:d8fa:ff5e:bce2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4064730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9847783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1466916151 (1.3 GiB)  TX bytes:3692989378 (3.4 GiB)
          Interrupt:193 

...
...
...
```Some information will no doubt be missing for you, since your network connection isn't working.

What to do next depends on how your LAN is configured. You might be using a DHCP server to allocate network addresses ... then again, you might not. Either way, you'll need to take a look at /etc/network/interfaces to see what's there.

Taking my machine as an example (again!), I've got...```
auto eth0
iface eth0 inet dhcp
```... indicating that the interface called "eth0" (attached to my Marvell ethernet card) should come up automatically, and use DHCP to get an address. Ubuntu takes care of the rest. It's never happened to me, but if my connection were to fail for some reason, I would now try **sudo ifup eth0** to try to force the interface up.

From there, you should be able to at least ping your default gateway, indicating that your network connection is working. Try ...```
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.7.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.7.100   0.0.0.0         UG    0      0        0 eth0

```The line that starts "0.0.0.0" (with a 'G' in the flags) is my default gateway for eth0. So I would try to ping 192.168.7.100. Whether you have internet access is up to the gateway really, so that's an issue for another day.```
# ping 192.168.7.100
PING 192.168.7.100 (192.168.7.100) 56(84) bytes of data.
64 bytes from 192.168.7.100: icmp_seq=1 ttl=64 time=0.178 ms
64 bytes from 192.168.7.100: icmp_seq=2 ttl=64 time=0.142 ms
64 bytes from 192.168.7.100: icmp_seq=3 ttl=64 time=0.152 ms
64 bytes from 192.168.7.100: icmp_seq=4 ttl=64 time=0.149 ms
...
...
```

How far through this post can you get? (Hopefully all the way :-) )

---

### Post by gojto on 2007-01-11
thx kidders but it seems that it doesnt recognize my adapter. when i type lspci it doesnt show anything. it doesnt even recognize my audio card thats not built on the MB. however in the etc/networking/interfaces there is: 

auto eth0
iface eth0 inet dhcp

im using a DHCP server to allocate the addresses (i have a router).

so whats next?? :)

thx
Gojto

---

### Post by kidders on 2007-01-11
Oh yuk. :-(

What would be perfect is the vendor/device codes, so I (or you) can take a look round the web for them for some help. Try **lshw -class network** to see if Ubuntu at least recognises your ethernet adapter as a network device. If it does, could you post the output of that command, along with the output of **lspci -n**. What I'm hoping is to be able to establish the vendor & device information from both chunks of garbage. Here's what I mean...

```
# lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: a
       **bus info: pci@00:0a.0**
       logical name: eth0
       version: 13
       serial: 00:1a:d3:5e:bc:e1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge ip=192.168.7.114 multicast=yes
       resources: iomemory:fdb00000-fdb03fff ioport:a400-a4ff irq:193
```From the PCI bus address, I can figure out which line of **lspci -n** refers to my own network card, and read off vendor "11ab", device "4320".

In your case, I'm hoping this will tell me exactly what version of exactly which network adapter you have, and all being well, I can come back to you with the name of a driver.

Did that make any sense?

---

### Post by gojto on 2007-01-11
ok thx. can i get those info in windows somehow?
thx
gojto

---

### Post by kidders on 2007-01-11
Emm... possibly. I couldn't begin to guess how though.

---

### Post by gojto on 2007-01-11
ok i tried to do so but this command does not show anything about the network adapter. so i can only tell you that i have a via p4pb400fl motherboard with a rhine 3 management. i tried to lookuo for the vendor in win and i came up with this data (not sure its the one you asked for): vendor "1106" device "3053". i hope this helps.

thx
gojto

---

### Post by kidders on 2007-01-11
Hey again,

Those numbers are perfect. :-) I've discovered two things:

[LIST]
[*]Drivers appear to be provided by the manufacturer. I stumbled accross them at [http://www.viaarena.com/](http://www.viaarena.com/)
[*]This seems odd to me, but my Linux kernel claims to include a module that should work for your adapter. What effect does **sudo modprobe via-rhine** have on your situation?
[/LIST]

---

### Post by gojto on 2007-01-12
hi again
ive tried "sudo modprobe via-rhine" and it doesnt do anything... so what next?

thx
gojto

---

### Post by kidders on 2007-01-12
Nothing? :-( No change to your hardware summaries, or the output of **ifconfig -a**? I guess it might be time to take a look at the vendor drivers. :neutral:

---

### Post by gojto on 2007-01-12
ok so i donloaded two drivers and dont know wich one is the right one:"VT6105_VT6106H_VT6106L_VT6106Sv28FVIA" and "VT6105Mv25FVIA". if you can tell me so and also how to install them it would be great...

thx
gojto

---

