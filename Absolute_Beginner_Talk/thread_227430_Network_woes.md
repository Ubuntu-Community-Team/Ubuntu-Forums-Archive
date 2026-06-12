---
title: "Network woes"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by The Shadow on 2006-08-01
I have an HP dv8000 Turion64 laptop with a realteck RTL8139 PCI Fast Ethernet card. Daper will recognize the card but will not allow me to access the internet or other computers on the network. when i attempt to click on the tolbar icon i get the error:

SIOCGIFFLAGS error: no such device.

I have attempted to enable the connection, i added the DHCP server  IP address. but i don't know where to go from here. any help available?

---

### Post by The Shadow on 2006-08-01
OK I solved the:

SIOCGIFFLAGS error: no such device

problem, but i'm back tothe main problem. I can't get my network card to work. not sure where to go from here.

any help?

---

### Post by halfvolle melk on 2006-08-01
What is the output of these?
```
ifconfig
sudo ethtool eth0
cat /etc/network/intefaces
```

---

### Post by The Shadow on 2006-08-03
Sorry it took so long to reply](*,) 

ifconfig results are:

etho Link encap:Ethernet HWaddr 00:0f:B0:BD:72:6E
      init addr:192.168.1.104 Bcast:192.168.1.225 Mask: 255.255.255.0
      inet6 addr: fe80:20f:b0ff:febd:726e/64 Scope:link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:355 errors:0 dropped:1407 overruns:0 frame:0
      TX packets:231 errors:0 dropped:0 overruns:0 carriers:0
      collisions:0 txqueuelen:1000
      RX bytes:62614  (61.1 KiB)  TX bytes:17743 (17.3 KiB)
      Interrupt:153 Base address: 0xa400

sudo ethtool results are:

Settings for eth0:
    Support ports: [ TP MII ]
     Supported link modes: 10baseT/ha;f 10baseT/full
                            100baseT/Half 100baseT/full
     Advertised auto-negotiation: Yes
      speed: 100Mb/s
     Duplex: Full
     Port: MII
     PHYAD: 32
     Transceiver: internal
      Auto-negotiation: on
     Supports Wake-on: pumbg
     wake-on: d
     Current messge level:0x00000007 (7)
     Link detected: yes

cat /etc/network/interfaces results are:

auto eth0
iface eth0 inet dhcp

auto eth1 
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by The Shadow on 2006-08-03
I re-booted my machine and now the network icon showes i am connected with eth0. it even showes a proper network address. But I still can not access the internet. I can't find anything about what sort of prototcols i might need to add or how to install them, but is it possible i don't have the TCP/IP protocol?

---

### Post by TFX360 on 2006-08-04
> **The Shadow said:**
> Sorry it took so long to reply](*,) 

ifconfig results are:

etho Link encap:Ethernet HWaddr 00:0f:B0:BD:72:6E
      init addr:192.168.1.104 Bcast:192.168.1.225 Mask: 255.255.255.0
      inet6 addr: fe80:20f:b0ff:febd:726e/64 Scope:link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:355 errors:0 dropped:1407 overruns:0 frame:0
      TX packets:231 errors:0 dropped:0 overruns:0 carriers:0
      collisions:0 txqueuelen:1000
      RX bytes:62614  (61.1 KiB)  TX bytes:17743 (17.3 KiB)
      Interrupt:153 Base address: 0xa400

sudo ethtool results are:

Settings for eth0:
    Support ports: [ TP MII ]
     Supported link modes: 10baseT/ha;f 10baseT/full
                            100baseT/Half 100baseT/full
     Advertised auto-negotiation: Yes
      speed: 100Mb/s
     Duplex: Full
     Port: MII
     PHYAD: 32
     Transceiver: internal
      Auto-negotiation: on
     Supports Wake-on: pumbg
     wake-on: d
     Current messge level:0x00000007 (7)
     Link detected: yes

cat /etc/network/interfaces results are:

auto eth0
iface eth0 inet dhcp

auto eth1 
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

__________________________________________________

I believe you can't work without a local loopback

Try adding to the top of /etc/network/interfaces

```
 sudo nano /etc/network/interfaces 
```

Add top the top

```

auto lo
iface lo inet loopback

```

After that reboot

```
 sudo reboot 
```

or

restart network

```
 sudo /etc/init.d/networking restart 
```

Can you ping a local address as test and post the results.

Your broadcast address is a bit wierd, I've only known it to be x.x.x.255


Hope it helps,


TFX

---

### Post by The Shadow on 2006-08-04
Local loopback is there, i left it out of the post because i didn't think it was important. I'm still a newb (only 1 week with Ubuntu) so i haven't figured out yet what is and isn't important.

I tried pinging a local adddress and got no response. I tried pining [www.google.com](www.google.com) and got no response. I tried pining 66.102.7.104 (a google ip address) and got:

Ping 66.102.7.104
From 192.168.1.103 icmp_seq=2 Destination Host Unreachable
66.102.7.104 pin statistics:
22 packets transmitted, 0 received +15 errors, 100% packet loss.

---

### Post by FsFrey on 2006-08-04
I asume your are connect to the internet through a router which probably gives out your IP schemes through it's DHCP service.  Do you have any other computers attached to the router? and can they get to the internet?

It looks to me like your router is giving out an invalid broadcast address.  I have always seen it as x.x.x.255 not x.x.x.225.  Look and see what your router or DHCP server is pushing to it clients.

---

### Post by The Shadow on 2006-08-04
Yes, i have three other computers (XP) on the same router and they all work fine. This one is set up as dual boot and under XPeverything works. So cable and router should not be the problem. I think i just don't have something set-up correctly but I'm not sure. The IP address looks consistant with my other machines. They are all withing the same range(one off). 

I  am a little confused about the server, and DNS entries in some of the config files. What should i be setting them to and how do i go abot doing so?

---

### Post by TFX360 on 2006-08-04
Summat like this:

```

iface eth0 inet static
  address 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  gateway 192.168.1.0

```

Ow, to be sure this replaces the total other eth0 statement. (assuming eth0 is you interface.)


Happy too help.

Kind regards,


TFX

---

### Post by FsFrey on 2006-08-04
> **TFX360 said:**
> Summat like this:

```

iface eth0 inet static
  address 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  gateway 192.168.1.0

```

Ow, to be sure this replaces the total other eth0 statement. (assuming eth0 is you interface.)


Happy too help.

Kind regards,


TFX



That was my next suggestion  :p

---

### Post by The Shadow on 2006-08-04
Pardon my ignorance, but where do i put this and how do i get it there?

---

### Post by eXisor on 2006-08-04
I'm coming quite late to this thread, but a few things come to mind. 

1) Your router is your DHCP server, but is it also your DNS server? 

2) What is your router's IP? Most likely it is 192.168.1.1 (192.168.1.0 is usually the modem?)

3) If my assumptions in 2 are correct, then change /etc/network/interfaces file to be (do a 'sudo gedit /etc/network/interfaces' and look for the 'iface eth0 inet' line) 

iface eth0 inet static
  address 192.168.1.250
  netmask 255.255.255.0
  network 192.168.1.1
  broadcast 192.168.1.255
  gateway 192.168.1.1

Note:  I changed your IP to be 192.168.1.250 to be sure the static ip is outside the range assigned by the router's dhcp service, usually only 50 ip's starting at 100, which ties in with the 104 it gave you. (Best is to check how many ip's it serves, and what the start and end numbers are).

If your router is also your DNS server, you may have to add the 
nameserver to your resolve.config file. Do a 'sudo gedit /etc/resolve.config' and add 'nameserver 192.168.1.1'

With this config, restart your network (do a 'sudo ifdown eth0 && sudo ifup eth0' and ping the router (ping -c 4 192.168.1.1
Any joy? Try ping the router by its name? Any joy?

Another thing to consider is that your router is likely not ipv6 capable, so type 'sudo gedit /etc/modprobe.d/blacklist' and add 'ipv6' to the bottom of the file. You'll need to reboot to get this going.

---

### Post by The Shadow on 2006-08-05
nope, NO Joy:-x 

after performing the operations above I still get:

ping -c 4 192.168.1.1
Results:
ping 192.168.1.1 (192.168.1.1) 56 (84) bytes of data

--- 192,168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

---

### Post by eXisor on 2006-08-05
try 

ping -c 4 192.168.1.0

what do you get?

---

### Post by The Shadow on 2006-08-05
the response was:

Do you want to ping broadcast? then -b

so I appended -b to the end of the command:

ping -c 4 192.168.1.0 -b

Response was:
WARNING: pinging broadcast address
ping 192.168.1.0 (192.168.1.0) 56(84) bytes of data.

--- 192.168.1.0 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

---

### Post by eXisor on 2006-08-05
Rats. Ok, maybe you got a Buffalo router. It's usually  192.168.10.1, so try that.

If that doesn't work, post your router make and model from the bottom of the router and I'll track it's manual down. This should be a synch once we get to ping it.

---

### Post by The Shadow on 2006-08-05
I can bring the router up from my windows machine. It is a Linksys router model number BEFSR81 VER 3 and it's status information is:

	Firmware Version:	2.51.1, Apr 25 2006	 	 
 	  	MAC Address:	00-0F-66-59-BB-93	 	 

Status
	 	 	 
 	 	 	Login Type:	DHCP	 	 
 	 	 	Internet IP Address:	69.73.7.117	 	 
 		 	Subnet Mask:	255.255.255.0	 	
 		 	Default Gateway:	69.73.7.1	 	
 	 	 	Static DNS1:	69.1.30.43	 	 
 	 	 	Static DNS2:	69.1.30.42	 	 
 	 	 	Static DNS3:	0.0.0.0	 	 
 	 	 	MTU:	1500

THE LOCAL IP ADDRESS IS 192.168.1.1

If any of this helps.

---

### Post by The Shadow on 2006-08-05
I interesting note;

I was observing the router client list and found that it did not contain an entry for my Ubuntu computer, even though the Ubuntu network connection status showed an address of 192.168.1.104. Sof I executed a sudo invoke-rc.d networking restart.

As the Ubunto combuter went through the network restart I repeatedly hit refresh on the router client list. low and behold, the client name and address showed up, only to disappear again after another refresh.

---

### Post by The Shadow on 2006-08-06
any more help available on this issue?

---

### Post by halfvolle melk on 2006-08-06
Does the router use mac filtering?

---

### Post by The Shadow on 2006-08-06
it can, but it is disabled

---

### Post by TFX360 on 2006-08-09
Try adding in /etc/network/interfaces under the last line under eth0

dns-nameservers x.x.x.x

Where x.x.x.x is the DNS ip from your provider and try pinging again to a few sites.

Can you actually believe this is NOT ADDED in the MANUAL PAGES of interfaces. Believed to be pre-programmed in our DNA. The interfaces reffers to /usr/share/doc/ifupdown/examples/network-interfaces which I can only find in a .gz file. Beats me.](*,) 

Feels like D'oh.

Kind regards,


TFX.

---

