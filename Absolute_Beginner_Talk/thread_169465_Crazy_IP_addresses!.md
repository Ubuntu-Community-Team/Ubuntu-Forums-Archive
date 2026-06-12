---
title: "Crazy IP addresses!"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-02
My i.p. addresses are going nuts! 
Here's my setup:     Linux Box ---------------Wireless Router-----Windows Box

my linux box is connected to the router via ethernet and my win box via wireless

Well see, my ip addresses need to remain constant so that samba can work.
But if they change, i have to do some extra steps each time to share my stuff.
1) how can i stop this madness?

2) why is this craziness occuring?

---

### Post by OffHand on 2006-05-02
[QUOTE=erik1397]My i.p. addresses are going nuts! 
Here's my setup:     Linux Box ---------------Wireless Router-----Windows Box

my linux box is connected to the router via ethernet and my win box via wireless

Well see, my ip addresses need to remain constant so that samba can work.
But if they change, i have to do some extra steps each time to share my stuff.
1) how can i stop this madness?

2) why is this craziness occuring?[/QUOTE]
ok, you have probably set Ubuntu to use DHCP. DHCP will configure your settings, including assinging you an ip. Go to system>administration>networking. Select you ethernet card and click properties. Change DHCP to static. Usually something like 192.168.0.X or 192.168.1.X

---

### Post by user1397 on 2006-05-02
[quote=subsonic_shadow]ok, you have probably set Ubuntu to use DHCP. DHCP will configure your settings, including assinging you an ip. Go to system>administration>networking. Select you ethernet card and click properties. Change DHCP to static. Usually something like 192.168.0.X or 192.168.1.X[/quote]
thanks, but what do i choose for subnet mask and gateway address?

---

### Post by OffHand on 2006-05-02
[QUOTE=erik1397]thanks, but what do i choose for subnet mask and gateway address?[/QUOTE]subnet 255.255.255.0 gateway is probably 192.168.0.1 (it's the address of your router) what is the output if you type ifconfig in the terminal? ```
ifconfig
```

---

### Post by user1397 on 2006-05-02
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:A5:31:9E
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fea5:319e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5238502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6335473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2559254158 (2.3 GiB)  TX bytes:1573577485 (1.4 GiB)
          Interrupt:23 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6442053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6442053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:552918303 (527.3 MiB)  TX bytes:552918303 (527.3 MiB)

---

### Post by OffHand on 2006-05-02
Do you have internet yet?

It's late here and I gotta work tomorrow. It's pretty simple to set up. 
I'm sure that there is someone else that can help you to set it up correctly or google it.
Goodluck.

---

### Post by user1397 on 2006-05-02
[quote=subsonic_shadow]Do you have internet yet?

It's late here and I gotta work tomorrow. It's pretty simple to set up. 
I'm sure that there is someone else that can help you to set it up correctly or google it.
Goodluck.[/quote]
yes...i've had internet for quite some time, maybe since march

---

### Post by AndyCooll on 2006-05-02
Ok here's mine.

Static IP address
IP address 192.168.2.3
Subnet mask 255.255.255.0
Gateway address 192.168.2.1

Judging by the ifconfig you gave us, I'd guess yours should read something like this:

Static IP address
IP address 192.168.1.2 (this can be whatever you chose between 2 and 255)
Subnet mask 255.255.255.0
Gateway address 192.168.1.1 (this is Ip address of your router)

And then as you add further boxes, you use the same basic system just giving each pc a different IP address

:cool:

---

### Post by user1397 on 2006-05-02
[quote=AndyCooll]Ok here's mine.

Static IP address
IP address 192.168.2.3
Subnet mask 255.255.255.0
Gateway address 192.168.2.1

Judging by the ifconfig you gave us, I'd guess yours should read something like this:

Static IP address
IP address 192.168.1.2 (this can be whatever you chose between 2 and 255)
Subnet mask 255.255.255.0
Gateway address 192.168.1.1 (this is Ip address of your router)

And then as you add further boxes, you use the same basic system just giving each pc a different IP address

:cool:[/quote]
Thanks, this really helped!

---

