---
title: "what next?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-08-25
i'm following this guide for server setup and i'm not sure where i get all the addresses from. can someone help me out with this please?

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)


[I]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
       [B] address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1[/B][/I]

---

### Post by k94382 on 2006-08-25
bump

---

### Post by A2A on 2006-08-25
Hi there,
Open up a terminal and type the following in there:
```
ifconfig
``` 
That should help you out.

Regards,

---

### Post by k94382 on 2006-08-25
i currently only have CLI so i dont think terminal will work.

---

### Post by k94382 on 2006-08-25
nvm, i see how it works. just type the command

---

### Post by A2A on 2006-08-25
Are you using a router or is this machine connected directly to a modem?

---

### Post by k94382 on 2006-08-25
using a router. all the machines, including the laptop which i want to turn into a server, are connected to the router.

---

### Post by A2A on 2006-08-25
Connect to the router from one of the other machines and open up the DHCP table.  That should give you a clue as to the IP assigned.

The only one you need to find is the "address".  The network, netmask, broadcast etc should be the same as in the example.

Regards,

---

### Post by A2A on 2006-08-25
> nvm, i see how it works. just type the command
 		 	 		 		 		 		 		 	 		 			 			 			 			 				[[IMG]http://www.ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://www.ubuntuforums.org/newreply.php?do=newreply&p=1419587")

So you're all set?

---

### Post by k94382 on 2006-08-25
oh ok... that makes everything easier. i will attempt everything tomorrow. time to sleep. nite

---

### Post by Jerome36 on 2006-08-25
I don't know how many different computers you have, or will have connected to your router, but you might want to set it up so each computer will always receive the same IP address from the router.  That's normally not the default setting.  If you're going to be using this computer as a server (I'm guessing just an Intranet server), you'll want static IPs, from the router.

---

