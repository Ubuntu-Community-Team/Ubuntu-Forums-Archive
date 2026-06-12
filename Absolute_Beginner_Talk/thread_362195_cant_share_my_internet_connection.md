---
title: "cant share my internet connection"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by stevr59 on 2007-02-15
hello every one i am having trouble with internet sharing i have 6.10 on my desk top and wins xp  and ubuntu 6.10 on my lap top i can share my connection with my lap top when it running ms xp but if i boot the lap top to ubuntu i cant share the conntion i tryed dhcp on bouth computer it didnt work i have tryed static ip on both that didnt work i am stumped now here is a copy of ifconfig from my desk top

desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BA:16:3B:22  
          inet6 addr: fe80::250:baff:fe16:3b22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1666416 (1.5 MiB)  TX bytes:401845 (392.4 KiB)
          Interrupt:185 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34671 (33.8 KiB)  TX bytes:34671 (33.8 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:216.76.248.127  P-t-P:209.215.46.194  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1612264 (1.5 MiB)  TX bytes:211063 (206.1 KiB)


i just installed 6.10 on the lap top and have not been able to connected with the desk top is there some thing else i need to insatll on the lap top or do i need to config some thing to get it to work i will try and get the ifconfig from the lap top as soon as i connect my modem to the lap top 
                                   cheers

---

### Post by louis_nichols on 2007-02-15
Let me see if I got the setup right:

Your desktop has Ubuntu and is linked to the web with one network card and to the Laptop with another. You configured it to share the internet connection and that works when the Laptop runs XP but not when it runs Ubuntu. As I understand, the desktop has a dhcp server to assign IPs. Is this correct?

The problem I see above is that eth0 doesn't have an IPv4 address. You need to configure one on the desktop, which runs as a firewall. Just give it 192.168.0.1. Then configure on the laptop both systems to assume the IP 192.168.0.2 and configure the firewall on the desktop to allow sharing of internet connection with this IP. It should work.

---

### Post by stevr59 on 2007-02-15
yes i have dhcp server enabled on the desktop and a static ip on the lap top, not sure how to configer a  IPv4 address. the only ipv4 i saw was for lo and it was 127.0.0.1 and as for a fire wall i dont see any one on  my copy of ubuntu i tried every thing and still its the same thing looks like i might have to start over again but not sure how to go about re doing the net work, all so i switched my modem blaster to my lap top and i still could not get on the Internet as i dont have kppp or groneppp install for the lap top so far this is not making any since as why some kind of dialer  don't come all ready installed so one can start updating  now the one thing i have not tried yet is to see if i can used the desktop as the server and the lap top running xp as the client and see if i can get on line whit the lap top normally if i an running xp on the lap top it is the server and ubuntu on the desk top is the client and that does work. thank for helping

---

### Post by louis_nichols on 2007-02-16
Well... One thing at a time. Unfortunatelly, I have no experience with ppp, but that does not seem to be an issue here.

The configuration of IPv4 in Ubuntu is done easily under System>Administration>Networking. There you have all your network connections listed and you just have to select the desired one, click properties, switch from dhcp assigned IP to static IP and enter the values. So this is what you have to do on your machine that is connected directly to internet, which is the firewall.

The firewalled machine needs only be set to aquire Ip by dhcp, which is default anyway, so no change there. The only thing is to configure the dhcp server correctly. But I think this should be ok by default, so once you set up the IPv4 on the firewall machine, things should work.

---

### Post by stevr59 on 2007-02-16
thanks i will try that but i got a few questions after i change it to static and type in my ip number what do i put down for the gateway address? all so on the main setting it has dns servers and host what do i put there and cant i return all the setting back to default since i been playing with all the setting for 2 days now. thanks for the help

---

### Post by stevr59 on 2007-02-16
ok i tryed what you said and it sill will not work here a copy of my ifconfig from the desk top 

steve@steve-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BA:16:3B:22  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe16:3b22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2043303 (1.9 MiB)  TX bytes:693160 (676.9 KiB)
          Interrupt:185 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1439355 (1.3 MiB)  TX bytes:1439355 (1.3 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:216.76.248.125  P-t-P:209.215.46.194  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1115831 (1.0 MiB)  TX bytes:432625 (422.4 KiB)
 think i may have messed up the setting i tried pinging each computer and no such luck  looks like i need to re set every thing back to default but not sure how to go about doing that

---

### Post by louis_nichols on 2007-02-16
> **stevr59 said:**
> ok i tryed what you said and it sill will not work here a copy of my ifconfig from the desk top 

steve@steve-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BA:16:3B:22  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe16:3b22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2043303 (1.9 MiB)  TX bytes:693160 (676.9 KiB)
          Interrupt:185 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1439355 (1.3 MiB)  TX bytes:1439355 (1.3 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:216.76.248.125  P-t-P:209.215.46.194  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1115831 (1.0 MiB)  TX bytes:432625 (422.4 KiB)
 think i may have messed up the setting i tried pinging each computer and no such luck  looks like i need to re set every thing back to default but not sure how to go about doing that

Ok. This looks right. Now it's a matter of configuring the firewalled machine For this, go to its network configuration and enter the following data (I know you have dhcp enabled, but I think that's the culprit)

IP: 192.168.0.2
netmask: 255.255.255.0
gateway: 192.168.0.1

Of course, you have to configure the machine to share the Internet connection. This is not very simple, but you can install a package called firestarter, which allows you to configure Linux's firewall and share the connection by simply checking a box.

---

### Post by stevr59 on 2007-02-16
Ok I Done All That You Said And I Still Cant Get On The Net With The Lap Top But I Am Now Able To Use The Net Work To Look At My Shared Files On The Desk Top So I Am Getting Some Where Not Unless I Don't Have Fire Starter Configerd Right I Been Playing With It , All So I Can Now Ping Bouth Computer Now But I Still Cant Share The Connection. Now On The Net Work Setting For The Server What Do I Put For The Gate Way Address May Be Thats My Proublem Not Shure What That Would Be

---

### Post by Quintin Riis on 2007-02-16
It is of great importance that you read the following.

[http://www.penny-arcade.com/comic/2002/10/11](http://www.penny-arcade.com/comic/2002/10/11)

You can't just 'share' the connection with ubuntu.  You'll need rules setup to handle routing.  Easiest would be to install firestarter, which is a nice frontend to iptables.  

How are the two computers connected?  If not through a hub or switch you'll need a crossover cable.  

Set the machine behind the firewall to use a static IP address, and set its DNS to be whatever the firewall machine is using.  Look at the file /etc/resolv.conf to see.

---

### Post by stevr59 on 2007-02-16
> **Quintin Riis said:**
> It is of great importance that you read the following.

[http://www.penny-arcade.com/comic/2002/10/11](http://www.penny-arcade.com/comic/2002/10/11)

You can't just 'share' the connection with ubuntu.  You'll need rules setup to handle routing.  Easiest would be to install firestarter, which is a nice frontend to iptables.  

How are the two computers connected?  If not through a hub or switch you'll need a crossover cable.  

Set the machine behind the firewall to use a static IP address, and set its DNS to be whatever the firewall machine is using.  Look at the file /etc/resolv.conf to see.

Ok sir i get your point. My two computer are connected by a cross over cable. And i do have firestarter installed and i got the dns set to what the config file said. Now i dont know what to put down for the gateway address on the setting for interface eth0 as of now i have 127.0.0.1 not shure if that is right or not. Thank's for helping.

---

### Post by Quintin Riis on 2007-02-16
Run the wizard in firestarter, it should help you configure the firewall.  As for getting the machines to talk to each other, they just have to have compatible IP addresses.

Something like the following should work.

a: 

address : 192.168.0.1
netmask: 255.255.255.0
gateway: n/a

b:
address: 192.168.0.2
netmask: 255.255.255.0
gateway: 192.168.0.1

Also, on 'b' you will need to edit /etc/resolv.conf and make it similar to the one on 'a' so that you can resolve hostnames.  If you want it all to work without copying anything, you could delete resolv.conf on 'b' and just put in "nameserver 4.2.2.2" 

Let me know if you need anything else.

---

### Post by stevr59 on 2007-02-16
> **Quintin Riis said:**
> Run the wizard in firestarter, it should help you configure the firewall.  As for getting the machines to talk to each other, they just have to have compatible IP addresses.

Something like the following should work.

a: 

address : 192.168.0.1
netmask: 255.255.255.0
gateway: n/a

b:
address: 192.168.0.2
netmask: 255.255.255.0
gateway: 192.168.0.1

Also, on 'b' you will need to edit /etc/resolv.conf and make it similar to the one on 'a' so that you can resolve hostnames.  If you want it all to work without copying anything, you could delete resolv.conf on 'b' and just put in "nameserver 4.2.2.2" 

Let me know if you need anything else.

ok thank's thatdid the trick as soon as i change the name server on the lpa top to mach the name server on the desk top it worked thank all you guys for helping

---

### Post by Quintin Riis on 2007-02-16
Glad I could help.  Always remember... computers communicate via IP addresses, not names.  So when you're troubleshooting, check out the DNS settings.

---

