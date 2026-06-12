---
title: "Shared Internet connection?"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by darkblue1893 on 2005-07-10
I have two computers connected to each other using ethernet cards and a crossover cable. The computer i am using for the gateway pc is the one with Ubuntu installed on it. THe second pc is using Win2000. I access the internet through a broadband cable connection. In network properties i have eth0 set as dhcp connection. eth1 has a static ip address. 

I have installed firestarter and set it to enable internet sharing but still the second pc cant access the internet. I dont think it is a hardware problem as internet sharing worked fine under windows.  Anyone know what the problem may be? Thanks.

---

### Post by Umbra on 2005-07-10
Assuming you recieve your internet from the eth0 interface do this in the console:

/sbin/iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
/sbin/iptables -A FORWARD -i eth1 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables-save > /etc/sysconfig/iptables

note: substitue ppp0 for the name of your conection, usually ppp0 is for dial-up, and pppoe for dsl, dont know what's yours.

Let's suppose your fixed ip in eth1 is 192.168.0.1, Go in the Win2000 machine, and setup the network conection with the following:

IP: 192.168.0.X (where X is more than 1)
Subnetmask: 255.255.255.0
Gateway: 192.168.0.1

And then add your DNS's.

---

### Post by apoc.feuer on 2005-07-11
[QUOTE=Umbra]Assuming you recieve your internet from the eth0 interface do this in the console:

/sbin/iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
/sbin/iptables -A FORWARD -i eth1 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables-save > /etc/sysconfig/iptables

note: substitue ppp0 for the name of your conection, usually ppp0 is for dial-up, and pppoe for dsl, dont know what's yours.

Let's suppose your fixed ip in eth1 is 192.168.0.1, Go in the Win2000 machine, and setup the network conection with the following:

IP: 192.168.0.X (where X is more than 1)
Subnetmask: 255.255.255.0
Gateway: 192.168.0.1

And then add your DNS's.[/QUOTE]

Hi Umbra, 

Thank you for sharing the tips, but I was not able to get the internet sharing up probably because i did not get the last part of command you have post it here right: 

[I]
root@sigmafirewall:/ # /sbin/iptables-save > /etc/sysconfig/iptables
bash: /etc/sysconfig/iptables: No such file or directory[/I]

Is there something wrong with the above command I typed in my terminal or is it my installation of Ubuntu has any problems? Anyway my sitatution is quite similar with darkblue1893 except that I use a switch rather than a crossover cable. 

Anyway, I did not switch on the firewall at this point of time, I am trying to ensure that the internet sharing is up before I configure firestarter. I receive the internet from eth0 (I have no problems accessing the internet) and my internal network is eth1. (eth1 is a brand new network  card) Anyway thank you for the guidance and sharing Umbra. I hope you advise me on this one thank you  :)

---

### Post by darkblue1893 on 2005-07-11
Thanks for replying. Tried all that but could not get the internet sharing to work. Have now formatted the HD and reinstalled windows xp, as i needed internet access for the second pc. Internet sharing worked straight away with windows. Will maybe try installing Ubuntu again and dual booting.

---

### Post by az on 2005-07-11
Next time, let's just suggest something like firestarter when someone who is not a linux sysadmin asks.  Especiall in the absolute beginner forum, please.

Firestarter is a grphical utility for firewalling and internet sharing (masquerading or Network Address Translsation)

You can install it from universe.

---

### Post by spd106 on 2005-07-13
Hi, check if your client pc has the default gateway setup.
ie

```
$route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

if you don't see the ip address or name of the intermediate pc under Gateway then you need to configure the routing.

```
$sudo route add default gw 192.168.1.1
```
Firestarter should take care of the rest.

Good luck

---

