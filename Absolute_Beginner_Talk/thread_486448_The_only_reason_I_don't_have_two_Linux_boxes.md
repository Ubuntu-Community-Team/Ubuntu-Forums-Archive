---
title: "The only reason I don't have two Linux boxes"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-28
The only reason I don't have two Linux boxes is because I can't get the darn things to share an internet connection.I have a linksys hub. If I have two windows boxes they can share a dsl connection. If I have 1 window box and one linux box they can share the connection(same config as the 2 win boxes. If I have to LInux boxes using the exact same config in the other examples they will not share the connection. The problem is on the win box I can force the IP 192.168.1.65 for some reason the lin box wont let me do this when I try to force an IP it will not connect to the internet so what ends up being the problem is I have to use the dhcp config witch always gives the same address 192.168.1.64. So the problem is when I have 2 lin boxes they both want to use this IP no matter what I try they will not let me pick my own IP. Does some one know how to lay the pimp hand down on my unruly linux pcs, so I can get rid of windows once and for all.

---

### Post by shearn89 on 2007-06-28
Have you set the Subnet mask and default gateway settings as well as the static ip? They both need the same subnet mask, with different IPs. I think you can set static ips by editing /etc/network/interfaces:
```

sudo gedit /etc/network/interfaces

#then set these settings:
auto eth0
iface eth0 inet static
        address <your ip>
        netmask 255.255.255.0
        network <first 2 sections of ip followed by 0.0 (normally)>
        broadcast *.*.0.255
        gateway *.*.0.1 <may be the ip of your router? not sure...>

```

---

### Post by swoll1980 on 2007-06-28
yes it's all the same config I use witrh the win box 'cept with different ip address

ip 192.168.1.64
net mask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.255.255

---

### Post by swoll1980 on 2007-06-28
when i use this config it will not connect   when I use dhcp it uses the same config and works. go figure

---

### Post by steveneddy on 2007-06-28
You don't need a Linksys **hub** - you need a Linksys **router**!

A router will give you a DHCP connection and [COLOR="Red"]many PC's can hook up to ONE DSL connection[/COLOR] when you use a **router**.

---

### Post by swoll1980 on 2007-06-29
> **steveneddy said:**
> You don't need a Linksys **hub** - you need a Linksys **router**!

A router will give you a DHCP connection and [COLOR="Red"]many PC's can hook up to ONE DSL connection[/COLOR] when you use a **router**.

The win boxes can use this hub to share a connection. Theres got to be a way for two linux boxes to share the connection with the same hub.

---

### Post by kakalaky on 2007-06-29
I believe firestarter has a gui ics configuration tool

---

### Post by swoll1980 on 2007-06-29
I had it configured. When I had static ip I could ping pc's but not the modem. So the lan was working fine it's the gateway that would not work. I made rule in the firestarter to allow 192.168.0.1 wich is the ip for my modem. no luck. my hub does not have an ip address. I even switched to pclinuxos thinking it was a ubuntu thing no luck there either. Is linux incompatable with a hub? If thats the case I guess I'm going to have to buy a router.Thats a last resort though.

---

### Post by Synflux on 2007-06-29
> 
ip 192.168.1.64
net mask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.255.255


Um,
Maybe that's a typo but if that's what you've actually got configured then it won't work as your ip address is in a different subnet to your gateway. You'll need to either change your subnet mask to 255.255.0.0 or, more likely, just correct your ip address to 192.168.0.64 or something in that range. Or maybe your gateway is actually 192.168.1.1? 

Either way there's something wrong in that config up there ^.

I hope that helps.

---

### Post by pallee on 2007-06-29
> **swoll1980 said:**
> 

ip 192.168.1.64
net mask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.255.255

If I'm not mistaken, shoulden't it be "adress" instead of "ip" 
Example: adress 192.168.1.64

Not sure if I'm right, but that is how my Ubuntu 5.0.4 is configured

Cheers, Paul

---

### Post by Synflux on 2007-06-29
> **pallee said:**
> If I'm not mistaken, shoulden't it be "adress" instead of "ip" 
Example: adress 192.168.1.64

Not sure if I'm right, but that is how my Ubuntu 5.0.4 is configured

Cheers, Paul

Yes, it should be ```
address <your ip>
``` as shearn89 put in their example.

However, even with that corrected, either the ip address or gateway is still set wrong.

:confused:

---

### Post by Wilfred on 2007-06-29
You may want to check this site:

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

Good luck!

---

### Post by xpod on 2007-06-29
I have two Ubuntu pc`s sharing one of our broadband connections with firestarter but i  have two network cards in one of the machine to do it..
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

If i wanted to connect more pc`s and use the hub i also have i would still need those two nic`s in the one machine although at the moment i just connect the second pc directly with a crossover cable.

A third machine my lad use has a completly separate ip address from our isp so i`ve managed to get by ok without a router up till now.

---

### Post by steveneddy on 2007-06-29
It's still a **whole** lot easier if you use a router.

---

### Post by xpod on 2007-06-30
> It's still a whole lot easier if you use a router.

If we did`nt have two seprate ip address(stb & sacm) then i`d have most certainly bought a router long before now.
In fact, i`ll still be buying one at some point but i`ve managed ok without one so far.

---

### Post by steveneddy on 2007-06-30
So, you have two different Ip addresses?

Static IP addresses?

With one DSL connection?

I think that the DSL connection has **ONE** [COLOR="Red"]DYNAMIC[/COLOR] IP address and if you used a router, it would give both PC's an IP address automatically.

Otherwise, one of your PC's needs to be the gateway, but you shouldn't need to have multiple NIC cards in the gateway PC.

My original argument still stands. For a network connection, DSL internet included, to be efficient and for both PC's to have the ability to be totally independent, you need a router. Trust me, you will save yourself TONS of headaches with a router.

It gives you an always on internet connection to a multitude of PC's connected to it and you can use the hub to run a small sub-network in another part of the house from one of the Ethernet connections in the router.

---

### Post by GeeZor on 2007-06-30
listen to synflux.. he is right!!

---

