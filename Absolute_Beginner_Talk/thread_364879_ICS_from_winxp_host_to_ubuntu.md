---
title: "ICS from winxp host to ubuntu"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by MattThLinuxNewb on 2007-02-18
Hi, i'm trying to share a 56k net connection from a winxp box to my Ubuntu machine. (i did manage to get modem going in ubuntu, but being limited to 14000bps by the linuxant modem driver is kinda unbearable.. :S) Anyway, I followed the instructions from annoyances.org on setting up Internet Connection Sharing with a winxp box as the host and another OS machine as a client (Ubuntu 6.06 in my case).  So far i've got the windows machine host (192.168.0.1) successfully pinging my machine (192.168.0.2), and vice versa, but ubuntu just can't seem to use the net connection! (e.g. firefox doesn't connect to any sites, and i can't ping any external IPs)
I set up ubuntu by going to System > Administrative > Networking and configuring the ethernet device manually like this:

Ip: 192.168.0.2
Subnet mask: 255.255.255.0
Gateway: 192.168.0.1

Any help would be great, i've really got no idea what im doing :confused: 
Thanks, Matt

---

### Post by Swab on 2007-02-18
Can you ping an internet IP address from the Ubuntu machine?  For instance you could try: 

ping 4.2.2.2 

If this works, then the problem is probably that you need to configure DNS.

Edit: I just noticed you already said you can't ping external addresses.. so just ignore me!

---

### Post by Bachstelze on 2007-02-18
```
cat /etc/resolv.conf
```

What does that give you ? You can also use DHCP on your Ubuntu box, the XP connection sharing acts as a DHCP server too.

---

### Post by MattThLinuxNewb on 2007-02-18
thanks for the fast replies all
HymnToLife, "cat /etc/resolv.conf" returns nothing..? Does that mean it doesn't exist?

---

### Post by MattThLinuxNewb on 2007-02-18
Wow, i switched eth0 back to DHCP and it worked straight off, i've got net access. (Thanks HymnToLife :) )
Ok so for anyone else having this problem i guess you could get the same result just by restarting Ubuntu (given that your ethernet configuration is DHCP)
Cheers :)

---

