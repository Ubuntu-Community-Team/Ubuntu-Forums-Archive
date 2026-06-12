---
title: "Ubuntu as a router &amp; DMZ Hosting"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by arrrghhh on 2007-10-02
Ok... so I followed a few different methods to get feisty to work as a dhcp server.  Long story short my router broke and I don't want to buy a new one.  

I am trying to get my PS3 to get online, and it seems I will need several ports forwarded to it, is there any way to simply pass all traffic directly to the PS3 as if it was just directly connected to the internet?  

I had to really struggle to get the internet working on the PS3, and now I have a NAT issue where it won't do anything because it's a "NAT: type 3" - essentially it doesn't have the proper ports forwarded.

Now I can't even get internet on the PS3!  I'm not sure how I broke it.

Here is my /etc/dhcp3/dhcpd.conf file
```

ddns-update-style none;

#option domain-name-servers 208.67.222.222, 208.67.220.220;

default-lease-time 86400;
max-lease-time 604800;

#authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
	option domain-name "ATHOME";        
	range 192.168.0.6 192.168.0.254;
        option routers 192.168.0.1;
	option domain-name-servers 208.67.222.222, 208.67.220.220;
	authoritative;
}

```

---

### Post by hyper_ch on 2007-10-02
Maybe have a look here how they done it:

[http://www.howtoforge.com/ubuntu6.06_firewall_gateway](http://www.howtoforge.com/ubuntu6.06_firewall_gateway)

---

### Post by arrrghhh on 2007-10-02
i actually found [this](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html) tutortial on how to use webmin... i'm likin webmin, just a lot of stuff to learn all at once!  i have A LOT to learn about routing, that's for sure.

---

