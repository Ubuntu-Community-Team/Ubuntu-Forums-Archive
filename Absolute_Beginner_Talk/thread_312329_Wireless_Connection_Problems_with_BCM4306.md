---
title: "Wireless Connection Problems with BCM4306"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Arthur Scrimshaw on 2006-12-04
Hi there - just installed 6.06.1 LTS from disk on a dual boot system (XP) on a seperate drive.
No problems with the install but I'm having problems connecting to the internet. PC has a Belkin F5D7000 card and connects via a Linksys WAG 354G gateway.
The card is correctly identified in the Device Manager as a BCM4306 broadcom device and in Network Settings is shown as active (eth1)
After booting up, I have to go into Network Settings each time and reset 'Default Gateway Device' to eth1 (which will be blank) - I have difficult getting it to accept this setting as it keeps blanking out the entry and it normally takes 3 or 4 attempts at resetting the gateway before it keeps this setting.
After this the connection is fine - until the next time I boot up.
This is my first experience with Linux and I'm very much a newb :( 

TIA

Simon

---

### Post by Arthur Scrimshaw on 2006-12-04
Right - a bit more info.

I find that by going into Networking, selecting eth1 as the default gateway, then selecting the properties of the wireless card. I disable, then enable the connection and it works fine.
Any ideas please?

Simon

---

### Post by dbott67 on 2006-12-04
Can you post the output of the following commands:
```
cat /etc/network/interfaces
```
```
ifconfig -a
```
```
cat /etc/resolv.conf
```
```
route -n
```

Thanks,
Dave

---

### Post by Arthur Scrimshaw on 2006-12-04
Hi Dave

Thanks for taking time out to help. I got the following outputs:-



simon@simon-desktop:~$ cat /etc/networking/interfaces
cat: /etc/networking/interfaces: No such file or directory

simon@simon-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8F:BC:83:16
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:11:50:44:20:FA
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe44:20fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14953610 (14.2 MiB)  TX bytes:390823 (381.6 KiB)
          Interrupt:10 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

simon@simon-desktop:~$ cat /etc/resolv.conf
search domain_not_set.invalid
nameserver 194.74.65.69
nameserver 194.72.9.34
nameserver 192.168.1.1

simon@simon-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
simon@simon-desktop:~$

thanks


Simon

---

### Post by dbott67 on 2006-12-04
> **Arthur Scrimshaw said:**
> Hi Dave

Thanks for taking time out to help. I got the following outputs:-



```
simon@simon-desktop:~$ cat /etc/networking/interfaces
cat: /etc/networking/interfaces: No such file or directory
```

My mistake Simon... it should be:
```
cat /etc/**network**/interfaces
```

```
simon@simon-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8F:BC:83:16
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:11:50:44:20:FA
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe44:20fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14953610 (14.2 MiB)  TX bytes:390823 (381.6 KiB)
          Interrupt:10 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
```

simon@simon-desktop:~$ cat /etc/resolv.conf
search domain_not_set.invalid
nameserver 194.74.65.69
nameserver 194.72.9.34
nameserver 192.168.1.1
```

Your DNS resolution looks weird.  Try editing it to the following:
```
gksudo gedit /etc/resolv.conf
```
```
**#** search domain_not_set.invalid
**#** nameserver 194.74.65.69
**#** nameserver 194.72.9.34
nameserver 192.168.1.1
```

```
simon@simon-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
simon@simon-desktop:~$
```

Your routing table looks good.

If you can re-post the output of

```
cat /etc/network/interfaces
```
and 
```
sudo lshw -C network
```
we should be able to figure it out.

-Dave

---

### Post by Arthur Scrimshaw on 2006-12-04
First bit:-

simon@simon-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



iface eth1 inet dhcp
wireless-essid linksys
wireless-key 0F3CC47345

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth1
simon@simon-desktop:~$

Then:-

simon@simon-desktop:~$ sudo lshw -C network
  *-network:0
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 03
       serial: 00:11:50:44:20:fa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-27-386 ip=192.168.1.65 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:f7ffc000-f7ffdfff irq:233
  *-network:1 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:13:8f:bc:83:16
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:e800-e8ff iomemory:f7fffc00-f7fffcff irq:217
simon@simon-desktop:~$


I tried editing the DNS resolution as suggested but it disabled my internet connection, so I put it back to what it was.

thanks 

Simon

---

### Post by dbott67 on 2006-12-04
Your **/etc/network/interfaces** looks good.

I'm wondering what is causing the problem connecting to the router.  The things that come to mind are:

1. What access points are in the vicinity and what is the signal strength?
Can you post the output of **iwlist scanning**?
```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              [COLOR="Red"]Frequency:2.437 GHz (Channel 6)[/COLOR]
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              [COLOR="Red"]Frequency:2.437 GHz (Channel 6)[/COLOR]
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

2. RFI/EMI Interference: are there any cordless phones (or other 2.4 GHz wireless devices) in the area that could be causing interference?  Microwaves, fluorescent lights, distance from AP can all cause poor signal strength.  Try getting as close as possible to the AP.  Also try other channels on your AP (the default is 6; try 1 or 11)

3. Wireless encryption: try turning off WEP and see what happens after you reboot.  Sometimes WEP can cause issues connecting.  If it connects properly, then you might try adjusting your key to something simple --- like a 128-bit, 13-character ASCII WEP key (try using 'mysecretwepkey' for your WEP key).  

All we're trying to do here is to systematically try to eliminate where the problem is:
- is it signal strength? move closer?
- is it interference? turn off other wireless devices, try changing channels
- is it encryption? turn it off

-Dave

---

### Post by Arthur Scrimshaw on 2006-12-05
Hi Dave

This is the result

simon@simon-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:9E:5E:13
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=100/100  Signal level=-134 dBm
                    Extra: Last beacon: 20ms ago

sit0      Interface doesn't support scanning.

simon@simon-desktop:~$



When using the machine in XP the signal levels are normally very high. I will try your other suggestions and report back.
Thanks again for your time.

Simon

---

### Post by dbott67 on 2006-12-05
Hi Simon,

I'll be offline for most of today & tomorrow, so it may take me a while to get back to you.  My wife & I are taking the kids on a little get-away to the [Great Wolf Lodge]("http://www.greatwolf.com/Locations/Niagara/").

-Dave

---

### Post by Arthur Scrimshaw on 2006-12-05
Hope you all have a great time - looks like a lot of fun!

Simon

---

