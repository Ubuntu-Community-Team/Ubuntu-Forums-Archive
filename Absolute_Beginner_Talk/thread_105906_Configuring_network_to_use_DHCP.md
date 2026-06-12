---
title: "Configuring network to use DHCP"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-19
I have a linksys etherfast 10/100 pcmcia network card that I hooked to my router and plugged into my laptop running a breezy server install. I have gotten it running with ifconfig eth0 up but I don't know how to get it to use DHCP to get an IP. I have configured it to get a static ip with ifconfig eth0 192.168.1.105 but I can only seem to ping the machines on my lan. How can I set up my network interface with dchp so that I don't have to enter my DNS servers by hand?

Also, what do I need to put in my /etc/network/interfaces? Right now it only has the loopback interface listed.

---

### Post by Kyral on 2005-12-19
```
sudo dhclient eth0
``` should do the trick

---

### Post by lleb on 2005-12-19
[QUOTE=wr0x2]I have a linksys etherfast 10/100 pcmcia network card that I hooked to my router and plugged into my laptop running a breezy server install. I have gotten it running with ifconfig eth0 up but I don't know how to get it to use DHCP to get an IP. I have configured it to get a static ip with ifconfig eth0 192.168.1.105 but I can only seem to ping the machines on my lan. How can I set up my network interface with dchp so that I don't have to enter my DNS servers by hand?

Also, what do I need to put in my /etc/network/interfaces? Right now it only has the loopback interface listed.[/QUOTE]

you can always edit the correct file:

/etc/network/interfaces

here is mine on my debian box, but should be basically the same in ubuntu

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.2.100
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

```

as you can see i have the iface eth0 inet dhcp commented out.  that is because at the house i keep a static IP, but when i go to LAN parties, or my LUGs install fests they work on dynamic.  

in that case, i just have to comment out the static info, uncomment the line for dhcp, then issue the following command:

```
/etc/init.d/network restart
```

in ubuntu you would just add sudo infront of that command as there is no "root" account.

---

### Post by lleb on 2005-12-19
sorry for the double post.  looks like the forum locked up on me.

---

### Post by wr0x2 on 2005-12-19
I have already edited my interfaces file to accept dhcp. When I try to run dhclient eth0, it sends a lot of dhcprequests on eth0, but ends up not finding anything. I know that the dhcp server on my router is working, because when I run "sudo dhclient eth0" on my main box, it finds a dhcpack from 192.168.1.1 first try.

---

### Post by Mr. Electric Wizard on 2005-12-19
Is DHCP running on rour router?
Have you troubleshot the ethernet cable out of the equation?

---

### Post by wr0x2 on 2005-12-19
yes, and yes.

I have got it on the network without DHCP by typing sudo ifconfig eth0 192.168.1.105. I know it is working because I installed sshd from the CD and when I ssh to 192.168.1.105 from my main box I can connect and run commands.

I still can't get DNS working though. Whenever I try to access an outside URL the system can't find it. I have the IPs for my ISPs dns servers, how would I enter those?

---

### Post by lleb on 2005-12-19
what does ifconfig say and what is the dmesg when you plug in the PCMCIA card as to what eth and what is the #, is it possible that you are trying to configure eth0 when you might need to be configuring eth1?

---

### Post by wr0x2 on 2005-12-19
The card makes a reference to eth0 when I plug it in. I'm very sure that eth0 is the correct device.

---

### Post by wr0x2 on 2005-12-19
Also, I have no /etc/resolv.conf file... Should I create one and add my dns servers in there, or should I do it in /etc/networking/interfaces?

---

### Post by Lambert on 2005-12-19
There seems to be some random/rare problems with dhcp and ubuntu. I haven't seen a solution posted yet by someone who has had problems.

If you can get setup with static then do that and add the lines to your interfaces file to set up nameserver. 

that works fine if you're stationary using one ap, if you travel then there are some options you have to set it up so resolv.conf can be set properly for each location, Post back if you need that and someone will give you the options you can use.

---

### Post by wr0x2 on 2005-12-20
Still doesn't work. I added my ISPs three nameservers to my interfaces file, but that doesn't do any good because I am not able to reach anything outside my lan. WTF is happening here. I guess I could do a reinstall but I'd prefer not to.

For the record, I have a linksys 4 port router w/ 802.11b.

---

### Post by lleb on 2005-12-20
[QUOTE=wr0x2]Still doesn't work. I added my ISPs three nameservers to my interfaces file, but that doesn't do any good because I am not able to reach anything outside my lan. WTF is happening here. I guess I could do a reinstall but I'd prefer not to.

For the record, I have a linksys 4 port router w/ 802.11b.[/QUOTE]

ok if your linksys is a router, then make that the first name server.  ie:  default = 192.168.1.1

from my earlier /etc/network/interfaces your could look something like this:

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

that should do the trick for you.  that is assuming you left the linksys router on its default settings of 192.168.1.1 with 255.255.255.0 as the subnet and the DHCP default of 192.168.1.100/199 meaning the first IP it feeds is .100 and will feed up to .199 so you would want a static IP well below the .100 thus the .10

hope that helps some.   FYI you are not messing with a wifi PCMCIA card are you?  this is ethernet or RJ45 connection on CAT5 or better cable yes?

---

### Post by wr0x2 on 2005-12-20
Yes, the connection is ethernet over cat5.

---

### Post by wr0x2 on 2005-12-20
Here's the relevant part of my etc/networking/interfaces file:

        iface eth0 inet static
        
        address 192.168.1.10
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

#dns
dns-nameserver (my three dns servers here)
default 192.168.1.1 (maybe I misunderstood what to put here?)

---

### Post by wr0x2 on 2005-12-20
All right, well I said screw it and tried to reconfigure again with DHCP. IT WORKS! I can ping google and other websites. I have no idea what was going on, but I think that my router may have been at fault, since I left it unplugged overnight last night.

---

### Post by Lambert on 2005-12-20
#dns
dns-nameserver (my three dns servers here)
default 192.168.1.1 (maybe I misunderstood what to put here?)

remove the default line and put this there

search the.domain.name.net

replace the domain.name.net with the domain name of the nameserver. If you don't know you can contact your isp or if you have a winxp machine you can open a cmd window and type ipconfig /all

With this interface file,  are you connected and can you ping an external site with the ip address?

---

### Post by lleb on 2005-12-20
glad it works.

---

