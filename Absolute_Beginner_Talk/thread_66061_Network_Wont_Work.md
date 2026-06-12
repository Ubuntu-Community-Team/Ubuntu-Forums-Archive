---
title: "Network Wont Work"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by Airpizza on 2005-09-15
First off heres some relevant specs

MSI  K8n Neo2 Platinum (Nforce 3 Ultra)
in that there are two ethernet ports - one Nvidia nforce one and one realtek one.
Ubuntu 5.04 **Edit 64bit version**
Cat5 into the nforce port connected to a switch which is connected to a router-all linksys

Both of the ports are recognized by Ubuntu as eth0 (nforce) adn eth1 (realtek)

Before installing Ubuntu i tried the Live version. When that loaded I could browse the internet without doing a thing to it.
Now when I installed Ubuntu it didnt like me and decided to not work :) 
When it got to the DHCP Part of the installation it failed, so I told it to continue anyways

Installation finishes and I try to surf the net...doesnt work


So I install the nforce drivers in hopes that that would fix it.

Nogo.. searched the forums for an hr or so and tried everything i could..still no

So i come to you !
heres what ifconfig gives me 

eth0 Link encap:Ethernet HWaddr 00:11:09:92:C4:43
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:930 errors:0 dropped:0 overruns:0 frame:0
TX pakcets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:97796 (95.5 KiB)  TX bytes:7866 (7.6 KiB)
Interrupt:22

eth1 Link encap:Ethernet HWaddr 00:11:09:92:C5:73'
UP BROADCAST MULTICAST MTU:1500 Metric :1
RX packets:0 errors :0 dropped: 0 overruns :0 frame:0
TX packets:14 errors:0 droped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:4788 (4.6 KiB)
interrupt:16 Base address:0x6000


lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436  Metric:1
RX packets:5583 errors:0 dropped:0 overruns:0 frame:0
TX packets:5583 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:507842(495.9 KiB)  TX bytes:507842 (495.9 KiB)

dhclient ends with No DHCPoffers  recieved. No working leases in persistent database - sleeping.

when i boot into windows the network runs fine.

Any suggestions? I'd hate to have to remove ubuntu because I couldnt connect to othe internet

---

### Post by gogomon on 2005-09-15
[QUOTE=Airpizza]First off heres some relevant specs

MSI  K8n Neo2 Platinum (Nforce 3 Ultra)
in that there are two ethernet ports - one Nvidia nforce one and one realtek one.
Ubuntu 5.04 **Edit 64bit version**
Cat5 into the nforce port connected to a switch which is connected to a router-all linksys

Both of the ports are recognized by Ubuntu as eth0 (nforce) adn eth1 (realtek)

Before installing Ubuntu i tried the Live version. When that loaded I could browse the internet without doing a thing to it.
Now when I installed Ubuntu it didnt like me and decided to not work :) 
When it got to the DHCP Part of the installation it failed, so I told it to continue anyways

Installation finishes and I try to surf the net...doesnt work


So I install the nforce drivers in hopes that that would fix it.

Nogo.. searched the forums for an hr or so and tried everything i could..still no

So i come to you !
heres what ifconfig gives me 

eth0 Link encap:Ethernet HWaddr 00:11:09:92:C4:43
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:930 errors:0 dropped:0 overruns:0 frame:0
TX pakcets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:97796 (95.5 KiB)  TX bytes:7866 (7.6 KiB)
Interrupt:22

eth1 Link encap:Ethernet HWaddr 00:11:09:92:C5:73'
UP BROADCAST MULTICAST MTU:1500 Metric :1
RX packets:0 errors :0 dropped: 0 overruns :0 frame:0
TX packets:14 errors:0 droped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:4788 (4.6 KiB)
interrupt:16 Base address:0x6000


lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436  Metric:1
RX packets:5583 errors:0 dropped:0 overruns:0 frame:0
TX packets:5583 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:507842(495.9 KiB)  TX bytes:507842 (495.9 KiB)

dhclient ends with No DHCPoffers  recieved. No working leases in persistent database - sleeping.

when i boot into windows the network runs fine.

Any suggestions? I'd hate to have to remove ubuntu because I couldnt connect to othe internet[/QUOTE]
 try doing a **sudo dhclient eth0** and see that gets you anywhere.

---

### Post by XDevHald on 2005-09-15
Great tip gogomon, also try using the command without eth0 at the end and see what results you get.

---

### Post by Airpizza on 2005-09-15
sudo dhclient  with and w/o eth0 at the end gives me the same answer in my post 
 No DHCPoffers recieved. No working leases in persistent database - sleeping.

---

### Post by cwaldbieser on 2005-09-16
[QUOTE=Airpizza]sudo dhclient  with and w/o eth0 at the end gives me the same answer in my post 
 No DHCPoffers recieved. No working leases in persistent database - sleeping.[/QUOTE]
If the Live CD worked for you, it might be worth booting into it and seeing what the /etc/dhcp3/dhclient.conf script it creates looks like.  You could compare it to the installed Ubuntu version of the same file and see if there is some difference.

---

### Post by Airpizza on 2005-09-16
....ok now the live cd's network doesnt work either!?!

---

### Post by Airpizza on 2005-09-16
ok i just found [This](http://www.ubuntuforums.org/showthread.php?t=58840&page=2&pp=10&highlight=nforce+network)

and got a static ip working by making it a static ip 192.168.1.11 and manually adding the DNS server (this was on the live version)

but then when i went into the installed version and to my suprise it j ust...worked

its using the dhcp too not the static...wierd. thx for the help guys: )

---

