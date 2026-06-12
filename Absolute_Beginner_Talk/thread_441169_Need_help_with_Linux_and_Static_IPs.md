---
title: "Need help with Linux and Static IPs"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Stormweaver on 2007-05-12
Hey guys,

I have an Ubuntu machine set up as a server for my house.  The biggest thing I am having an issue with is that I am running a Teamspeak server on this machine.

Last night for whatever reason we had a major bump on our net connection so I did a reboot of all the hardware and computers to make sure nothing lingered (First reboot of only Modem and Routers caused some people to not reconnect to the net)

I've not gotten Teamspeak back up since, and found this morning that the server is not on the internal IP it was/needs to be on.


I need the system on 192.168.1.100 -- Linksys says I have to set that up in the computer not the router.  Also, when I look at the DHCP Client Table on the Router, the Ubuntu machine is not listed at all, BUT I still have internet connection.  Any ideas what to do here?


Thanks

---

### Post by MrHorus on 2007-05-12
> **Stormweaver said:**
> 
I've not gotten Teamspeak back up since, and found this morning that the server is not on the internal IP it was/needs to be on.

I need the system on 192.168.1.100 -- Linksys says I have to set that up in the computer not the router.  Also, when I look at the DHCP Client Table on the Router, the Ubuntu machine is not listed at all, BUT I still have internet connection.  Any ideas what to do here?


You can set it up using ifconfig but if you are using DHCP then your router might just kick out an address anyway.

Regardless, try:
```

sudo ifconfig 192.168.1.100 netmask 255.255.255.0

```

You may need to tweak the netmask a little, depending on what subnet your router is using internally.

---

### Post by duckville on 2007-05-12
Not sure of the exact settings for your router but usually you can see the assigned IP addr. for the MAC addr. of the NIC of the PC.

What you might be able to do is edit the router config. so that it assignes the ip addr. that you want to the MAC addr. if the NIC of the PC. That should clear it up.

---

### Post by steve.horsley on 2007-05-12
Mr. Hous misssed the (required) interface name. Try:
> sudo ifconfig eth0 192.168.1.100 netmask 255.255.255.0
but it's probably easier (and also permanent) to set it in the GUI - System->Administration->Network. Choose the network connection and click Properties.

---

### Post by Stormweaver on 2007-05-12
Ok... Before I try doing this, what could cause the Router to not see the system, yet the system be connected to the internet through the router?


Stormweaver

---

### Post by Stormweaver on 2007-05-12
Also how do I get Linux to tell me where it is currently parked on the router since the router can't see it?

Ya know like in Windows you could do ipconfig and it would show you the info?


Stormweaver

---

### Post by steve.horsley on 2007-05-13
The command **ifconfig** will tell you what the current system IP address is. **route -n ** will tell you the current routing table. **cat /etc/resolv.conf** will tell you the current DNS configuration,

---

