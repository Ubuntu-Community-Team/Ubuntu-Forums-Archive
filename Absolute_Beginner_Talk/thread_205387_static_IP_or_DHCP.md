---
title: "static IP or DHCP"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-06-28
i have to boxes one a old desktop with XP on it and another a new laptop wit UBUNTU on it.
juz wanted to install SAMBA to share the two.
while browsing thru the forums i came around static ip and dhcp 
i m juz not able to get these terms.
can sumbdy explain these and also which type should i use?

---

### Post by kb3hkg on 2006-06-28
The two terms refer to how the computer recieves its IP address. DHCP assigns it an address from a pool of IP's. Static IP is when it is always assigned the same IP address, this is usually done by assigning a specific address to the NIC's MAC address.

---

### Post by xtacocorex on 2006-06-28
Static IP gives the computer a set IP address that doesn't change. So if you set your computer up with the IP 192.168.0.10 then it will stay that way.

DHCP dynamically sets a computers IP address by leasing one out to it, so for one lease period you may be 192.168.0.20 and then on another lease you might be 192.168.0.15. This is an over-exaggeration of what it actually does and there are more things about DHCP that are complicated, like the ability to have it set a certain IP for a MAC address.

Unless you set up your network in Ubuntu by telling it an IP address, you probably have it set to DHCP (the default) and I would keep that.

---

### Post by MaximB on 2006-06-28
I in the other hand would reccomand you to use static IP address in order to connect the two boxes. (static on both machines)
that way you can always connect them without having to change the ip address every time.
but the drawback is that you couldn't connect to the internet with thouse ip address cuz there is a chance that some computer over the glob already connected with this static ip and duplicated IP's are not allowd over the internet.
p.s
you can connect your ISP (internet service provider) and ask for perment IP address (static (reserved) from dhcp).

---

### Post by Iowan on 2006-06-28
As usual, the answer is: it depends.
It's probably easier to assign static addresses to each machine.  As mentioned, when the internet gets involved, things complicate.  If you have a router/firewall, it will (probably) be configured to get a dynamic address from your ISP.  It is probably capable of being a DHCP server for your network.  I installed a DHCP server on my home network server (which serves two client machines) primarily to learn how to do it.  So, it depends on whether you just want to get two machines talking with minimum fuss, or whether you want to get more acquainted with networking...

---

