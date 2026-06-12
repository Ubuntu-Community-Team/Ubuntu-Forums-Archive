---
title: "Internet conection problem(wire)"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Dagagad on 2008-03-02
I work at a university in Korea and am on the University network.
I had problems with vista connecting also and maybe Ubuntu is having similar problems. On Vista you would have to write in the IP, gate, etc manually. After it wouldn't connect on ubuntu using the DHCP(begins with D anyway) automatic connection, I wrote them in on the Static IP form.

My specs are

hp pavillion dv6000
amd turion 64/2 TL-50
Nvidia graphics card(not sure which one)
120 GB hard drive
2gb ram

When I ran the ifconfig comand in the terminal, I got the folowing..


etho     link encap: ethernet        Hwaddr: 00:1B:11:D9:18
            inet addr: 219.253.180.xx  Bcast 219.253.180.xx 
            Mask:255.255.255.xxx
            inet 6 addr: fe80: :21b:24ff:fell:d918/64 scope:link
            UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
            RX packets: 29888 errors:0 dropped:0 overruns:0 frame:0
            TX packets: 2299   errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes: 3080095(29mb) TX bytes: 150221(146.7)

lo        link encap: local loopback
          inet addr: 27.0.0.1 Mask: 255.0.0.0
          inet 6 addr:    ::1/128    Scope: Host    
          UP LOOPBACK RUNNING MTU:16436       Metric:1
          RX packets:1429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0    txqueuelen:1000
          RX bytes: 148555(145kbs) TX bytes: 148555(145kbs)


This is probably something simple that I am missing..thx for the help.

---

### Post by Dagagad on 2008-03-02
bump

---

### Post by jan quark on 2008-03-02
please post the results of the following terminal commands

```
iwconfig
```

```
sudo lshw -C network
```

```
cat /etc/network/interfaces
```

---

### Post by candtalan on 2008-03-02
if it may help, here is a copy of my own ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:5F:BD:A8
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe5f:bda8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4116305 (3.9 MB)  TX bytes:590801 (576.9 KB)
          Interrupt:20

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:288 (288.0 b)  TX bytes:288 (288.0 b)


I am no expert with this. The only thing that looks really differernt with your ifconfig output is yours has xx whatever where mine has numbers or a zero. I hav eno idea if that is important though. hth

---

### Post by Dagagad on 2008-03-02
Ok I did all the tests and also the IF config again. Thanks for taking the time to reply:) The wire connection is the priority now as I rarely use wireless.


IF CONFIG

john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:11:D9:18  
          inet addr:219.253.180.34  Bcast:219.253.180.63  Mask:255.255.255.224
          inet6 addr: fe80::21b:24ff:fe11:d918/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5562899 (5.3 MB)  TX bytes:320841 (313.3 KB)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:216146 (211.0 KB)  TX bytes:216146 (211.0 KB)


IWCONFIG

john@john-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@john-laptop:~$ 

CAT /ETC/NETWORK/INTERFACES


john@john-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback





iface eth0 inet static
address 219.253.180.34
netmask 255.255.255.224
gateway 219.253.180.63













auto eth0
john@john-laptop:~$ 


SUDO LSHW -C NETWORK

john@john-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:3b:66:d4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
john@john-laptop:~$

---

### Post by Dagagad on 2008-03-02
bump..anybody have any idea why its not working?

---

### Post by Dagagad on 2008-03-02
OK I have no idea what is wrong with this...does anyone have a suggestion?

---

### Post by bumanie on 2008-03-02
I suspect it is a problem with ipv6. I know of a couple of others users who have had this issue through University Networks. In fact there are a number of home users who have had this issue also.
Disable ipv6 by 
> sudo gedit /etc/modprobe.d/blacklistAt the end of the gedit list type 
balcklist ipv6
Save and reboot. That will hopefully work. 
If it doesn't you can get the gedit list back and delete what you have added and save again, this way thre is no chnage to your system.
As I said, I am aware of this working with University Networks in the past.
Good Luck.

---

### Post by Dagagad on 2008-03-02
I tried that Bunamie but it didn't work. Thanks for you help anyway.

In the netwok box..beside the wired connection IP address it says 'SU....'

anybody know what that means and if it is connected to the problem?

---

### Post by bumanie on 2008-03-02
Sorry, can't help with that one.

---

### Post by candtalan on 2008-03-02
> **Dagagad said:**
>  In the netwok box..beside the wired connection IP address it says 'SU....' anybody know what that means and if it is connected to the problem?

I am really just guessing, I am a network non expert, but you are connecting into a relatively complex network, and if you get the IP and mask numbers wrong you will get nowhere fast. I had a small taste of this recently when I was trying to run a print server device on an alien network, I got the network number wrong. Wasted a lot of time chasing shadows.

Carefully verify that the numbers such as
inet addr:219.253.180.34 Bcast:219.253.180.63 Mask:255.255.255.224
are really all ok, particularly the .34 and .63 and .224
for your subnet.

I wonder if the 'SU...' indicates a 'subnet' item?

good luck

---

### Post by Dagagad on 2008-03-02
Those are the same numbers I use for vista so I'm not sure what is wrong. I just talked to a guy down the hall who says 7.10 won't connect on his pc also. He said to try 6.06. I'll try that. In the mean time, any other ideas?

---

