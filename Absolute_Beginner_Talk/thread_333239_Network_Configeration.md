---
title: "Network Configeration"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Brian R. on 2007-01-07
Have installed ubutu 6.06 on old machine (only os on it) have now installed a network card a Realtek8139, and the system can see it, and i can open the configuration window. But i need help with the configeration. I want to connect to a windows xp machine by cross over cable. So do i use a DHCP or Static IP address, if static what should i put in for the IP address, subnet mask, and do i need a Gateway address. Plus does any body know what configurayions i need on the windows machine.
Thank you.

---

### Post by Koybe on 2007-01-07
You won't have any dhcp server so you got to set both at static. You need nothing special but both pc get in the same network.

Ubtuntu :
address 192.168.1.1
netmask 255.255.255.0

Win XP :
address 192.168.1.2
netmask 255.255.255.0

No gateway needed on any computer.

That's all.

---

### Post by eggert on 2007-01-07
Unless your xp mahine is running a DHCP server you should use static IP.  Just pick one from the 192.168.1.*** range and mask 255.255.255.0  Simply put, the gateway address is for addresses other than are specifically known to your computer, so for example if you are going to connect to the internet through your xp machine you should put the address of it as default gateway but if you only plan to connect to that one computer I don't think you need it.
For connection between the two your best bet is samba.  See [www.ubuntuguide.org](www.ubuntuguide.org) for helpful instructions on setting that up.

hth. Eggert

Koybe can obviously type a bit faster than me. :)

---

### Post by Koybe on 2007-01-07
> **eggert said:**
> Koybe can obviously type a bit faster than me. :)

But you got more ideas... you talked about samba :D

---

