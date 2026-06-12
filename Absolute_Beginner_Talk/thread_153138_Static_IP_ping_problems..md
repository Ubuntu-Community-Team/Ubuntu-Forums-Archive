---
title: "Static IP ping problems."
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by slapshot on 2006-03-31
Hi everybody, 

I am a Linux (and Ubuntu) beginner. I installed Ubuntu, without problems, on a PIII Acer Veriton 5100 Chipset 82801BA and it seems to work ok. Now, my only problem is that Ubuntu cannot ping any pc of my LAN and the other pc cannot ping Ubuntu. 

I seem I configured ok the Ubuntu network with static IP but there is no way to go and ping. Also the gateway (192.168.1.1) is impossible to ping. 

The weird thing is that Ubuntu can ping itself, for example ping 192.168.1.12 works well, otherwise I have Destination Host Unreachable.

Ifconfig tell me that eth0 is RUNNING and the IP, subnet mask, bCast are ok. There is a particular, Tx and Rx are all 0.

I tried to deactivate and reactivate with no success. I verified Iptables and it is all in ACCEPT. 

With no ping there is no chance to surf Internet, so I believe it is not a DNS problem. 

Really have no idea of how to do. Can you help me ?

BTW, I tried with Knoppils Live and it worked well, I could surf and ping the LAN without problems. 

Thanks in advance.
Antonio

---

### Post by jolger on 2006-03-31
try disabling ipv6 if it is not already done by doing this:

gedit /etc/modprobe.d/aliases

find the line:

alias net-pf-10 ipv6

and replace with:

alias net-pf-10 off #ipv6

else make sure that the right device is configured correctly by looking here:

gedit /etc/network/interfaces

make sure that the "primary network interface" is configured like it should be example from my server:

# The primary network interface
iface eth0 inet static
        address 10.13.15.21
        netmask 255.255.255.0
        gateway 10.13.15.1
        network 10.13.15.0

where the ip address of the server is 10.13.15.21
the subnetmask is 255.255.255.0
the gateway is 10.13.15.1
and the network on wich the computer is on is 10.13.15.0

---

### Post by slapshot on 2006-03-31
Thanks for your reply. I'll try to off ipv6 and restart the pc but without no success. The interfaces file is correct and similar to yours.

Any other ideas that I can try ?

Bye
Antonio

---

### Post by slapshot on 2006-04-01
Anyone can help me ? I really does not know what I have to do ;).

Thanks.

---

### Post by alamba on 2006-04-01
Post netstat -rn. You might need to add a default route.
route add default gw <your-gateway-ip-address>

A

---

### Post by lilalu on 2006-06-12
You should also set

..
gateway 192.168.1.x
network 192.168.1.0
broadcast 192.168.1.255
..

---

### Post by rccharles on 2006-06-14
[QUOTE=slapshot]
I seem I configured ok the Ubuntu network with static IP but there is no way to go and ping. Also the gateway (192.168.1.1) is impossible to ping. 
[/QUOTE]

[QUOTE=slapshot]
The weird thing is that Ubuntu can ping itself, for example ping 192.168.1.12 works well, otherwise I have Destination Host Unreachable.
[/QUOTE]
The message "Destination Host Unreachable" means that there are different subnets on your lan. One subnet cannot access another subnet without going through a router. ( At least, I think so. ) 

I suggest you do an sudo ifconfig on each machine and see that the network mask and IP addresses are appropriate. Use ipconfig on Windows.


[QUOTE=slapshot]
BTW, I tried with Knoppils Live and it worked well, I could surf and ping the LAN without problems. 

[/QUOTE]

I gather Knoppils is the Italian version of Knoppix.  Knoppix defaults to dynamic ip addresses.  Try changing to a dynamic address. 
sudo gedit /etc/network/interfaces
...
iface eth0 inet dhcp
...

Change the eth0 line to the above to get you TCP/IP info from dhcp and delete extra stuff (address, netmask, etc ). Then issue these two commands to reset:

sudo ifdown -a
sudo ifup -a

or reboot

sudo ifconfig 

to see what happened

Another idea...
You could run Knoppils again and when you network works, do an:
ifconfig
to see the working parameters.

Robert  :)

---

