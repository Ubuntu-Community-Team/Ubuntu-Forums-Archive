---
title: "Input Connection Settings"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by PureW on 2006-10-18
Hello, I have Ubuntu Dapper Drake, 6.17.25 or something similar. My problem is that ever since I moved and recieved internet access through a LAN with a set ip-address I cant connect to the internet. Previously I connected through a router with DHCP and that worked flawlessly. I have a dual-boot with Windows and internet in windows with the settings below is fine. I have recieved a document with my internet settings, perhaps you could tell me where to enter these? I have tried and tried but no matter where and how I input this, internet doesnt work:
Computer name: PurewComputer
IP-Address: 193.11.220.25
Netmask: 255.255.254.0
Default Gateway: 193.11.220.1
Domain: sis.onenet.se
Nameserver (DNS) 1: 193.11.230.41
Nameserver (DNS) 2: 83.140.87.2

I have tried pinging my own ip-address, and I recieve answer, but when pinging the gateway, it times out (the troubleshouting from my isp told me to do this).

EDIT: I am connected through a LAN-jacket in my apartment.

---

### Post by DSn0wMan on 2006-10-18
How are you connecting to the internet?

ex: modem (cable/dsl) -> computer

or modem (cable/dsl) -> router -> computer

---

### Post by PureW on 2006-10-18
I simply plug my network cable into the jacket in the wall.

---

### Post by DSn0wMan on 2006-10-18
Can you post your interfaces file (/etc/network/interfaces).

```
sudo gedit /etc/network/interfaces
```

---

### Post by PureW on 2006-10-18
> **DSn0wMan said:**
> Can you post your interfaces file (/etc/network/interfaces).

```
sudo gedit /etc/network/interfaces
```

Aye:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 193.11.220.209
netmask 255.255.254.0
gateway 193.1.220.1

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by DSn0wMan on 2006-10-18
That looks good to me. I dont know what to say. Maybe try giving it a restart. Otherwise the setup looks fine. If it still dosn't work try posting the output of ```
ifconfig
```

---

### Post by PureW on 2006-10-18
ifconfig:
```

Link encap:Ethernet HWaddr 00:13:0F:01:B0:30
inet addr:193.11.220.209 Bcast 193.11.221.255 Mask:255.255.254.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 fram:0
TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:50 Base address:0xe400

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:29 errors:0 dropped:0 overruns:0 frame:0
TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2552 (2.4 KiB) TX bytes:2552 (2.4 KiB)

```

---

### Post by DSn0wMan on 2006-10-18
That looks fine. Can you ping the gateway?

One thing I noticed, is that you are using a class C address, and a class B netmask. I would double check with your provider to see if the netmask they gave you is valid.

for example the netmask for a class C address (not subnetted)of 192.168.X.X would be 255.255.255.255

The netmask for a class B address (not subnetted) 172.29.X.X would be 255.255.255.0

I could be wrong because it's been a while since I studied these things, thats the only thing that sticks out to me.

---

### Post by mips on 2006-10-18
That netmask looks a bit funny to me. Late here will have a proper look in the morning.

Btw who is your ISP, provide a link ?
What brand/model router do you have ?
What doe the output of **lspci - v** say ?

---

### Post by PureW on 2006-10-19
I tried pinging the gateway, and it timed out.

I doubt the ip-address and netmask is wrong since the ip-address and netmask works in windows.

And my ISP is a company in sweden that students can rent apartments from. I don't have any router since I have a 10/10 LAN-jacket in my wall which I connect directly to my network-card.

Here is the output from lspci -v: (I'll only show the ethernet part since I guess that's the part you're interested in, and because Im copying this manually.)
```

0000:11:0 Ethernet controller: ALi Corporation M5263 Ethernet Controller
Subsystem: ASRock Incorporation: Unknown device 5263
Flags: bus master, medium devsel, latency 32 IRQ 58
I/O ports at e400 [size=256]
Memory at febfec00 (32-bit, non-prefetchable) [size=256]
Capabilities: [50] Power Management version 2

```

---

### Post by mips on 2006-10-19
Maybe have a look here, [http://www.ubuntuforums.org/showthread.php?t=83710](http://www.ubuntuforums.org/showthread.php?t=83710)

Just because things work in Windows does not mean they are correct. I have seen windows flaunt a few tcp/ip RFC rules before in my life.

---

### Post by PureW on 2006-10-21
The strange thing is that I once accidentally switched to "Recieve ip-address from dhcp", and then the internet worked fine, until the guy with the dhcp-server shut his computer down.

---

