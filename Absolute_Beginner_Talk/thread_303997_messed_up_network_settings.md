---
title: "messed up network settings"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-11-21
I've broken my network settings for Ubuntu Linux, And can no longer connect to the internet from it, only on windows (oh joy)
can someone provide me with original Ubuntu files for the network, and instruct me where to place them.

I messed them up whilst trying to get ubuntu to recognize a different network at my mother house. But as everything with linux is, it was very difficult, down right impossible to get right.

---

### Post by Jimmey on 2006-11-21
Well, here's what I'd do.

Boot into Windows. Run the command prompt (it differs; Usually in Start>All Programs>Accessories>Command Prompt, or try running "cmd" or "command" using Start>Run).

Then type the command "ipconfig/all". This will tell you the infromation you probably need to know about your working network connection. Write it down :-)

Then boot into Ubuntu. Type the command "less /etc/network/interfaces/". Write what ever you see down :-)

Then type the command "less /etc/resolv.conf". Also, write that down. :-)

Then paste here what you wrote down, and where you copied it from.

---

### Post by Captain Kirk76 on 2006-11-21
OK, well here is what i get from CMD in Windows

Windows IP Configuration

        Host Name . . . . . . . . . . . . : pooter
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : VIA Rhine II Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-09-1D-00-DA-0D

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Physical Address. . . . . . . . . : 00-08-54-3C-08-20
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 20 November 2006 16:26:53
        Lease Expires . . . . . . . . . . : 20 December 2006 16:26:53

Ethernet adapter Hamachi:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Hamachi Network Interface
        Physical Address. . . . . . . . . : 7A-79-05-59-83-3C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 5.89.131.60
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        Default Gateway . . . . . . . . . :
        DHCP Server . . . . . . . . . . . : 5.0.0.1
        Lease Obtained. . . . . . . . . . : 21 November 2006 15:21:42
        Lease Expires . . . . . . . . . . : 12 November 2007 15:21:42


Ubuntu bit..

less /etc/network/interfaces/ - No such file or directory
less /etc/resolv.conf - No such file or directory

---

### Post by Jimmey on 2006-11-21
Well, it seems that you have a fair few active network interfaces in your pooter, there :-P

Well, there are three. Namely
Ethernet adapter Hamachi;
Ethernet adapter Local Area Connection;
Ethernet adapter Local Area Connection 2.

I say namely - These are the names that are given to the interfaces by Windows.

In Linux, they'll be called eth0, eth1, and eth2, most probably. 

I'm not sure what the Hamachi interface is being used for :-P
The first Ethernet adapter is connected to a LAN?
And the second one is not being used. 

There are two ways to configure your network in Ubuntu. The first being by using the GUIs in System>Administration>Networking menus. Here's how you'd go about doing that.

First off, you'll have to figure out which interface is which. Your LAN interface will most probably be eth1, so let's get that done first.

Select eth1 and click "Properties". Under "Configuration", make sure you select the "DHCP" option. Then, if you're using Dapper, I think you should be able to quit that menu, and click the "Activate" button. If not, just type > sudo ifup eth1 into a terminal :-P

Secondly, you want to configure your Hamachi interface. This is just a guess, but it seems more likely that this interface will be eth2. Simply do the same as you did with eth1.

Thirdly, you want to specify a DNS server. This is, from what I can gather, 192.168.1.1

---

### Post by scc4fun on 2006-11-21
> **Captain Kirk76 said:**
> OK, well here is what i get from CMD in Windows

Windows IP Configuration

        Host Name . . . . . . . . . . . . : pooter
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

<snip Local Area Connection 2 />

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-08-54-3C-08-20
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 20 November 2006 16:26:53
        Lease Expires . . . . . . . . . . : 20 December 2006 16:26:53

I believe that is the same Ethernet network card that is in my wife's Compaq computer. It looks like your computer is connected to a Linksys(?) router. Linux should be able to connect without any problems.

> **Captain Kirk76 said:**
> Ethernet adapter Hamachi:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Hamachi Network Interface
        Physical Address. . . . . . . . . : 7A-79-05-59-83-3C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 5.89.131.60
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        Default Gateway . . . . . . . . . :
        DHCP Server . . . . . . . . . . . : 5.0.0.1
        Lease Obtained. . . . . . . . . . : 21 November 2006 15:21:42
        Lease Expires . . . . . . . . . . : 12 November 2007 15:21:42
> **Jimmey said:**
> I'm not sure what the Hamachi interface is being used for :-P

Hamachi is a program that takes care of LAN connection over the internet (using VPN technology). There is a Windows and a Linux program for it available [here]("http://www.hamachi.cc/download/list.php").

> **Captain Kirk76 said:**
> Ubuntu bit..

less /etc/network/interfaces/ - No such file or directory
less /etc/resolv.conf - No such file or directory

Not sure why they don't show up.

> **Jimmey said:**
> Well, it seems that you have a fair few active network interfaces in your pooter, there :-P

Well, there are three. Namely
Ethernet adapter Hamachi;
Ethernet adapter Local Area Connection;
Ethernet adapter Local Area Connection 2.

I say namely - These are the names that are given to the interfaces by Windows.

In Linux, they'll be called eth0, eth1, and eth2, most probably. 

<snip>
The first Ethernet adapter is connected to a LAN?
And the second one is not being used. 

There are two ways to configure your network in Ubuntu. The first being by using the GUIs in System>Administration>Networking menus. Here's how you'd go about doing that.

First off, you'll have to figure out which interface is which. Your LAN interface will most probably be eth1, so let's get that done first.

Select eth1 and click "Properties". Under "Configuration", make sure you select the "DHCP" option. Then, if you're using Dapper, I think you should be able to quit that menu, and click the "Activate" button. If not, just type  into a terminal :-P

Secondly, you want to configure your Hamachi interface. This is just a guess, but it seems more likely that this interface will be eth2. Simply do the same as you did with eth1.

Thirdly, you want to specify a DNS server. This is, from what I can gather, 192.168.1.1

For the Hamachi interface, I would suggest downloading the Hamachi for Linux client software from the link listed above and configuring it as you did in Windows. Other than that, follow Jimmy's advice for setting up the Realtek network interface.

---

### Post by Captain Kirk76 on 2006-11-21
Hamachi has no use for me in Linux, i only use Hamachi in Windows as it helps playing multiplayer games online.

Also, i have 3 active connections (2 physical, 1 emulated by Hamachi) A network card (or NIC) and a connection integrated onto my Motherboard which is dodgy and doesnt work. (hence the media disconnected, and the network card)

---

