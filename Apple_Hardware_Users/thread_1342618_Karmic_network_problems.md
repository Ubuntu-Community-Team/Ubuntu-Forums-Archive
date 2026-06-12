---
title: "Karmic network problems"
date: 2009-11-30
forum: Apple Hardware Users
---

### Post by Epamek on 2009-11-30
I just installed 9.10 on a black 4.1, and I have absolutely no way to connect to the internet.

The first problem I found, which is apparently common among macbook users, is that I don't have any drivers installed and a wireless option doesn't even show up under Network Manager.  I even replicated my airport network after clicking new by the (blank) list of wireless networks to no avail.

I would be able to install the drivers necessary to detect the signal, but my ethernet isn't working either!  I have an ethernet cable plugged directly from my wall (no modem or router) to my Macbook, yet I'm getting no signal.  The default network, eth0, isn't giving a response at all.

I get nothing but zeros for my IPs and such when I use iwconfig or ifconfig.  Is there any way to manually install the necessary drivers from a flash drive or something?  How would I go about doing that?

---

### Post by linuxopjemac on 2009-12-01
did you have internet on eth0 with the liveCD ?

---

### Post by barnex on 2009-12-01
> **Epamek said:**
> 
I get nothing but zeros for my IPs 

I have a similar problem. I my case, it's because I'm behind a D-link router that Ubuntu wrongfully sees as a DNS nameserver. That's why all IP's get resolved to 0.0.0.0. You can check if this is also the case for you by typing:

```
sudo cat /etc/resolv.conf
```

if it says something like "nameserver 192.168.x.x", Ubuntu thinks your router is a DNS server. I could temporarily fix this by:

```

sudo su
echo "nameserver 193.74.208.65" > /etc/resolv.conf
exit

```

where 193.74.208.65 is the nameserver of my local ISP, you may want to replace it with yours. I'm still looking for a better, permanent fix, but I hope this helps you at least a bit.

---

### Post by linds2009 on 2009-12-02
I have also encountered the same problem

---

### Post by barnex on 2010-01-03
Follow-up: I could work around the problem by adding ```
ipv6.disable=1
``` to my grub options. The problem was that my D-link router did not play nice with ipv6. I could permanently fix the issue by updating my router firmware. Then, even with ipv6 enabled again, all worked well.

I hope something similar does the trick for you as well...

---

