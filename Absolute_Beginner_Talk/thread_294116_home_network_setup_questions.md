---
title: "home network setup questions"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-11-06
I have a desktop (ubuntu) and a laptop (win xp sp2). The desktop is connected to the internet through a dsl modem with ethernet connection.
I am interested in connecting the laptop to the desktop for file sharing mostly (dont need internet on both machines necessarily).
My first thought (and low cost one) was to buy a second NIC for the desktop and connect the two of them with a proper ethernet cable, so that I would have something like:
(www)---dsl modem eth0---->(ubuntu)------eth1 lan----->(windows)

1. Can ubuntu handle two nic's or am I going to run onto trouble?
2. Since I am a noob can you please tell me the steps for configuring the two machines?
3. Do I need to install anything in ubuntu or windows for file/game  sharing?If yes how?

---

### Post by steve.horsley on 2006-11-06
This should work fine. Ubuntu can handle many NICs provided you get Linux compatible ones, and most are. You will need a small hub to connect the two PCs to, or an Ethernet crossover cable to connect them directly to each other (a crossover cable has different connections to a normal Ethernet cable inside).

You could possibly configure the Ubuntu eth1 as a DHCP server and leave the laptop as a DHCP client, but I don't know how to configure a DHCP server on Ubuntu.

Or you could configure both PCs with static IP addresses, on a different network number to the network on your ADSL modem, e.g. 192.168.2.1 and 192.168.2.2. On Ubuntu, System->Administration->Networking, and configure the address there. netmask should be 255.255.255.0.

I suggest we leave internet access for the laptop until you have the basic connectibity working.

Once the boxes can ping each other, it's time to do the file sharing. Probably easiest is to install samba file sharing on Ubuntu. [http://ubuntuguide.org/wiki/Dapper#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Dapper#How_to_share_folders_the_easy_way)

---

### Post by geokok1981 on 2006-11-06
Thanks for the answer. However I would like to try something else first before going for the nic.
I have connected the desktop through ethernet to the modem.
I have connected the laptop through usb to the modem. (its a speedtouch 530v6)
Both of them have static ip.
Can I make them see each other in that way? I instaled samba automatically when I chose to share folders in Ubuntu. I tried to ping the win machine but no luck (zone alarm perhaps?) The win machine can ping the ubuntu one and the desktop is visible in " Network places" However "OK" button is greyed out when choosing it in order to add it.....
Any tips here?

---

### Post by Carlos Santiago on 2006-11-06
No, you cannot use the speedtouch modem as a HUB.
You should buy a 2nd NIC, that should work just fine, and with no additional software. 
Or you can connect the modem to your desktop via USB, and use the spare NIC to connect to your Laptop. This will need some configuration, and possible need some drivers.
The easiest and cheapest way (cause time is money) is to buy a 2nd NIC.

Then use, for example, these IP addresses:
(www)---dsl modem eth0---->(ubuntu)------eth1 lan----->(windows)
           ETH1/USB0              ETH0                Ethernet
           Auto/DHCP        IP:192.168.0.1         IP:192.168.0.2
      (given by the ISP)  MASK:255.255.255.0   MASK:255.255.255.0
                                          DEF GATEWAY:192.168.0.1
                             DNS: The same DNS defined on Desktop


Connect the two PCs using a crossover cable.
The try to ping 192.168.0.1 from 192.168.0.2 or vice versa
If your ping is OK, now u can easly share your Internet connection. Run the commands:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from (ETH1 or USB0 in the above example)

# echo 1 > /proc/sys/net/ipv4/ip_forward

to activate IP forwarding.

---

