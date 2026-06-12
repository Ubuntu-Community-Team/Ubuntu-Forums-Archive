---
title: "Transient Resolver failure?"
date: 2008-12-27
forum: Arch and derivatives
---

### Post by mips on 2008-12-27
Edit: Never mind. I disbaled dhcp and somehow while it was still running it overwrote the resolv.conf file I edited earlier. I was pulling my hair out :)

---

### Post by handy on 2008-12-27
Do you use the /etc/resolv.conf.head file to control resolv.conf ?

---

### Post by mips on 2008-12-28
> **handy said:**
> Do you use the /etc/resolv.conf.head file to control resolv.conf ?

Probably not as i don not recall ever looking at /etc/resolv.conf.head.

I usually install with DHCP and when done switch to an all static config for network & dns.

---

### Post by handy on 2008-12-28
You can specify your DNS addresses there & they get written to resolv.conf every time the network is started, like so:

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

I wish I could have done that back in the early days with ubuntu, I had a hell of time with DNS issues.

---

### Post by mips on 2008-12-28
> **handy said:**
> You can specify your DNS addresses there & they get written to resolv.conf every time the network is started, like so:

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

I wish I could have done that back in the early days with ubuntu, I had a hell of time with DNS issues.

Thanks, I will keep that in mind if I use dhcp ;)

---

### Post by handy on 2008-12-28
> **mips said:**
> Thanks, I will keep that in mind if I use dhcp ;)

I've never had the permanent IP address type of account with an ISP.

Though now I only have the IPCop box's IP address presented to resolv.conf via the resolv.conf.head nameserver line.

---

### Post by mips on 2008-12-28
> **handy said:**
> I've never had the permanent IP address type of account with an ISP.



My router gets a dynamic address from the ISP which it NATs to local addresses on the LAN side. My router does offer lan ip's via dhcp but I prefer keeping all my lan side ips static which is only for 4 devices.

---

### Post by fwojciec on 2008-12-28
I used to have static IP configured individually on each of my computers but now I just configure my router (DD-WRT) to assign IPs based on MAC addresses.  I find it to be a more elegant solution -- especially for my laptops, since I can simply use wpa_supplicant and dhcpcd to have a roaming wifi capability and be able to connect to any network using the same procedure/tools and still have persistent IP addresses when I connect to my home network.  [This]("http://bbs.archlinux.org/viewtopic.php?id=59004") is the script I use, by the way.

In addition I have pdnsd configured to serve as local DNS cache so that DNS lookups are quicker -- this is where resolv.conf.head comes in useful, since I need it to add 127.0.0.1 to the top of resov.conf.

I like this configuration -- it works better than all my previous configurations which were, usually, static IP at home and dhcpcd everywhere else.

---

### Post by Dr Small on 2008-12-28
> **mips said:**
> My router gets a dynamic address from the ISP which it NATs to local addresses on the LAN side. My router does offer lan ip's via dhcp but I prefer keeping all my lan side ips static which is only for 4 devices.
Me too, since I hate dealing with dynamic ips. It causes too much confusion for the family members wanting to connect to each other's computers...

---

### Post by handy on 2008-12-28
I've managed to avoid the can of worms that wireless is capable of presenting, on our home LAN thus far as we just use cables.

IPCop has the ability to assign IP's to MAC addresses, & I think you can bind more than one MAC address to a single IP as well.  These capabilities are beyond my needs.

---

