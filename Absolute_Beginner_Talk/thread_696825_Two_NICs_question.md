---
title: "Two NICs question"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Older1 on 2008-02-14
I've seen and read posts similar to this question, but none seem to address my situation specifically.

I have one NIC in my machine set to a static address from our ISP that bypasses our router via a switch, which I use to check SharePoint sites we've set up as if I'm seeing them from outside the business.

I added a second NIC set to roaming mode to receive an address from our internal DHCP server.

My idea is to be able to _switch between NICs_, depending on what I want to do: use one, eth1, with the static public IP, to get around the router. The other, eth0, DHCP assigned address, to use internally to access local network mapped drives.

Since I'm relatively new to Linux systems, simplistic explanations will be greatly appreciated.

Thank You!

---

### Post by OffAxis on 2008-02-14
I'm not totally clear on what your question is...
You've got the cards configured already; are you asking how to switch between the two?
You can use
```
sudo ifdown eth0
sudo ifup eth1

```

or vice-versa.

---

### Post by Older1 on 2008-02-14
Yes, I want to switch between NICs, but even after doing sudo ifdown eth1, and sudo ifup eth0, eth1 is still active even after reboot.

Copied from Terminal:

wjw@wjw-ln-800k7:~$ sudo ifdown eth1
[sudo] password for wjw:
ifdown: interface eth1 not configured
wjw@wjw-ln-800k7:~$ sudo ifup eth0
ifup: interface eth0 already configured

It IS listed first in the Network Settings box; does that make a difference?

---

### Post by LRT on 2008-02-14
OffAxis, i think that yes he is asking how to switch between the two, so using this makes sense:

```
sudo ifdown eth0
sudo ifup eth1
```

but i don't think he really needs to do this.  i have two nics on my machine both on different subnets where i get internet from one and a lan connection from the other... both of them are always up at the same time... maybe Older1 needs to be more specific...

---

### Post by LRT on 2008-02-14
oh! ok... try this instead:

```

sudo ifconfig eth1 down
```

hope this helps

---

### Post by Borbus on 2008-02-14
You don't need to switch between them. Have them both up, you will be able to access both networks simultaneously.

---

### Post by Older1 on 2008-02-14
Ok, first, my face is RED! I didn't have eth1 configured to DHCP, it was Roaming Mode. So now I can sudo ifdown eth1, and it releases the DHCP address. I just can't get eth0 up with sudo ifup eth0.
I will try sudo ifconfig eth0 up.

BTW: I don't want both up at the same time; I want either/or.

Thanks so far for the help.

---

### Post by Older1 on 2008-02-14
Ok, so I can do sudo ifconfig eth1 down, and it does deactivate eth1. However, when I do sudo ifconfig eth0 up, I get nothing. In other words, no active eth0.

Oh well, maybe it's just as fast to re-configure one interface from static to dhcp when the need arises. <sigh>

Tomorrow is another day......

---

### Post by OffAxis on 2008-02-14
> In other words, no active eth0.


Does it show up in 
```
ifconfig
```
?

> but even after doing sudo ifdown eth1, and sudo ifup eth0, eth1 is still active even after reboot.

**ifup/down** is transitory; if you reboot the network is reinitialized and you start from ground zero again.

to make the changes permanent (or more permanent, if you spent 90% of your time on one) you would edit the **/etc/network/interfaces** file.

You would add something like:
```

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address <your static ip here>
        netmask <your subnet here>
        gateway <your gateway here>
        pre-up ifconfig eth1 down
```

(I don't have time to check that so don't bust my chops if it's not right)

I seem to recall you can do the same thing in an initialization script or an rc.local file...

---

### Post by Older1 on 2008-02-15
Well, I think I've got this conundrum figured out.After making the NIC active I want to use, I need open up the active NIC and re-enter the DNS server IPs.

For some reason, the DNS server IPs on the NIC with the static IP address populate to the NIC which I have set to DHCP.

Anyway, thank you all for your tips and help. It was very much appreciated!!

---

