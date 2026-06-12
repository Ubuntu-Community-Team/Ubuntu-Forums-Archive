---
title: "Default gateway problem"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Laddin on 2007-10-21
Hi, i can't set up a default gateway in my Ubuntu. When i type "sudo route add default gw xxx.xxx.xxx.xxx" it tells me "SIOCADDRT: No such process". Can anyone help me?

---

### Post by mikeyphi on 2007-10-21
Sorry - don't quite understand your problem...
Are you trying to set up your internet connection or is this a Server OS problem?

---

### Post by Laddin on 2007-10-21
I'm trying to set up an internet connection. I set my DNS in file "/etc/resolv.conf" and ip with "sudo ifconfig eth0 xxx.xxx.xxx.xxx netmask xxx.xxx.xxx.xxx". That works fine, but when I try to set up default gateway with "sudo route add default gw xxx.xxx.xxx.xxx" I get this error:

```
SIOCADDRT: No such process
```

---

### Post by shad0w_walker on 2007-10-21
Are you running a standard Ubuntu setup with a X? If you are then just goto System > Administration  > Network

You can setup all your network settings from there.

---

### Post by Laddin on 2007-10-21
I'm running Gutsy Gibbon. 

I tried it throught System > Administration > Network after installation, but ping to google.com returned "Unknown hostname" and ping to google ip returned "Network is unreachable." So I decided to set up my connection by console and got stuck at "SIOCADDRT: No such process" :/

---

### Post by mikeyphi on 2007-10-21
> **Laddin said:**
> I'm running Gutsy Gibbon. 

I tried it throught System > Administration > Network after installation, but ping to google.com returned "Unknown hostname" and ping to google ip returned "Network is unreachable." So I decided to set up my connection by console and got stuck at "SIOCADDRT: No such process" :/

Reboot then open Network manager and confirm that all the settings are correct. If yes, check obvious things like plugs/power/router
Post some details of the Internet setup....Network card/modem or router/ direct or via proxy/ etc

---

### Post by Laddin on 2007-10-21
I checked the settings in Network manager once again, they are correct, exactly the same as on Windows which I'm running now on same machine. I have a direct connection with public ip. I really dont know what is wrong, maybe this will help:

```

ipconfig(win):

IP Address: 192.179.177.XXX
Sub Mask: 255.255.255.0
Default Gateway: 192.168.92.37


ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:16:D3:5B:FC:3B  
          inet addr:193.179.177.xxx  Bcast:193.179.177.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21200 (20.7 KB)  TX bytes:4279 (4.1 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:79:89:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 Memory:f8000000-f8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



route:

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

193.179.177.0   *               255.255.255.0   U     0      0        0 eth0
```

---

### Post by mikeyphi on 2007-10-21
Doesn't seem to be an Internet address on eth1 Is it positively enabled in Network manager?
What make/version of card?

---

### Post by Laddin on 2007-10-21
eth1 is a wireless card, i need to set up eth0(wired card). I'm using Broadcom netlink card...

---

### Post by mikeyphi on 2007-10-21
> **Laddin said:**
> eth1 is a wireless card, i need to set up eth0(wired card). I'm using Broadcom netlink card...

That's strange - from your previous it looked as though you had a working connection on eth0!

I know that Broadcom is not well supported - try to post more exact details of the card.
There are many problem threads on Broadcom wireless cards, if you find you wired details it might be that someone out there has got a fix!!

---

### Post by Laddin on 2007-10-21
Well I have Broadcom BCM5787M Gigabit Ethernet , if it helps

---

### Post by mikeyphi on 2007-10-21
There is a possible driver here: [http://www.broadcom.com/support/ethernet_nic/netlink.php](http://www.broadcom.com/support/ethernet_nic/netlink.php)
(tg3)

---

### Post by shad0w_walker on 2007-10-21
Give this a try:

1. Open /etc/network/interfaces in the editor of your choice (Will require sudo)
2. Modify this to suit your networks IP addresses:

auto eth0
iface eth0 inet static
 address 10.0.0.45
 netmask 255.255.255.0
 network 10.0.0.0
 broadcast 10.0.0.255
 gateway 10.0.0.1

3. Past into the file (Remove or comment out any existing eth0 entry
4. Run this to restart the network components and make them read the new details
```
sudo /etc/init.d/networking restart
```

5. Sit back and enjoy (Hopefully)

---

### Post by Laddin on 2007-10-22
> **mikeyphi said:**
> There is a possible driver here: [http://www.broadcom.com/support/ethernet_nic/netlink.php](http://www.broadcom.com/support/ethernet_nic/netlink.php)
(tg3)

Those drivers are allready installed, I'll try to set up "/etc/network/interfaces" and let you know...

---

### Post by Laddin on 2007-10-22
Well, hopefully not :(

When i enter "sudo /etc/init.d/networking restart" command i get this error:
```
* Reconfiguring network interfaces... 
SIOCADDRT: No such process
Failed to bring up eth0.
                                                                         [ OK ]

```


I set the "/etc/network/interfaces" exactly like this:
```
auto eth0
iface eth0 inet static
address 193.179.yyy.xxx
netmask 255.255.255.252
broadcast 193.179.yyy.255
network 193.179.yyy.0
gateway 192.168.92.37
```

But network card seems to be ok, according to lshw:
```
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:5b...
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5787m-v3.23 ip=193.179.yyy.xxx latency=0 module=tg3 multicast=yes

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:79:89:21
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated
```

I really don't know what to do any more :(

---

### Post by shad0w_walker on 2007-10-22
That's an odd one. Unfortunately I've hit a limit in my knowledge so hopefully a bump will attract someone with some answers.

---

### Post by Laddin on 2007-10-24
Well, I think I whats causing the problem. When i try to set Default gateway from same ip class as my ip(example: 193.179.123.123 - gateway: 193.179.123.10). I dont get any errors, but of course internet doesnt working since my gateway is "192.168.92.37." Thanks for help...

---

### Post by steve.horsley on 2007-10-24
As a matter of the way IP routing works, your default gateway must be on the same network as your own NIC. Having an IP address on 193.x.x.x and a default gateway on 192.x.x.x will not work.If the default gateway is not on your local network, then the PC still doesn't know how to forward packets to the defautl gateway.  This is the cause of your (rather misleading) error message.

P.S. 
Looking at the values from your interfaces file, your local network only supports 2 host addresses - 193.179.yyy.253 and 193.179.yyy.254. Your default gateway should be whichever address your computer isn't.

---

### Post by Laddin on 2007-10-24
Well, now i'm confused a bit, because these settings with default gateway not being on the same network work perfectly on Win. 

Earlier I used to have my IP on the same network as default gateway. But then I asked my ISP to give me a static public ip. He gave me a new ip and left gateway on a different network.

So how should I set up my connection?

---

### Post by steve.horsley on 2007-10-24
Is your subnet mask right at 255.255.255.252? 
If so, is your IP address one of the two I said in my last post?
If so, try setting the default gateway to the otehr address like I said.

If not, I can't tell you the right numbers to put in because you won't tell me the right other numbers. ou can leave the thitd octet as yyy if you want to preserve some anonymity.

---

### Post by Laddin on 2007-10-24
Subnet mask 255.255.255.252 is right, however connection on windows work with mask 255.255.255.0 too. And i found out that mask "255.255.255.252" was the second thing which was causing the problem. With these new setting I'm not getting any errors:
```
auto eth0
iface eth0 inet static
address 193.179.yyy.50
gateway 193.179.yyy.252(253)
netmask 255.255.255.0
broadcast 193.179.yyy.255
network 193.179.yyy.0

```

But still can't access the internet. I think i'm going to ask my ISP about that gateway...

---

### Post by Laddin on 2007-10-25
Hehe at last, got the right gateway from my ma ISP. My connnetion is now working!

Thanks for help everyone :popcorn:

---

