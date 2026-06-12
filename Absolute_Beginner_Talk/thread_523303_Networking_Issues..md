---
title: "Networking Issues."
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-08-11
i ahve a Desktop Pc on a wireless connection, and im trying to get my laptop to use this internet connection Via Ethernet cable, i cant seem to get it to work.
below is a poor diagram of my situation.

----- = wireless
____= wired

Laptop ____ Desktop -----router = internet

ive tried DHCP.

on my desktop ive put the Ethernet wired connection as.

192.168.0.1
255.255.255.255
Blank

on the laptop ive put static again

192.168.0.2
255.255.255.255
192.168.0.1

is there anything i am missing?
i understand a Pc on a router is harder to share network than if on a wired connection.

but is this possible?

---

### Post by PilotJLR on 2007-08-11
First make sure the laptop can ping the ip address of the desktop.

Then make sure pinging the router does not work.

Then turn on IP forwarding on the DESKTOP using:
```

sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
exit

```

Then see if you can ping the router - this will hopefully now work.


This is not persistent across reboots, so edit /etc/sysctl.conf to make it stick.

---

### Post by PilotJLR on 2007-08-11
Woah! Also got some bad subnet masks there.
Just use 255.255.255.0 instead to keep it simple.


Your wireless network should NOT be on this same subnet.

---

### Post by skymera on 2007-08-11
o yeah.
soh

i try them now!!

my wireless connection is DHCP...
so whzt should the subnet mask be?

also hpow should i configure my Pc's wired connection.
and the alptops.

i tried pinging router.

but it says

From 169.254.4.196 icmp_seq=1 Destination Host Unreachable =S

nor can i ping my desktop...

---

### Post by PilotJLR on 2007-08-11
What is the address and mask of the desktop's wireless interface now?

---

### Post by PilotJLR on 2007-08-11
It looks like you removed the wired static addresses...

Let's make sure we pick the right addresses. On you desktop, what is the ip addrs and mask of the wireless interface?

You can leave the wireless conection as-is... just need to know what address and mask it is right now.

---

### Post by skymera on 2007-08-11
ok ifconfig produced this...

```

ra1       Link encap:Ethernet  HWaddr 00:17:3F:28:E5:CE  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe28:e5ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:497132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265986 errors:2 dropped:2 overruns:0 carrier:0
          collisions:2118 txqueuelen:1000 
          RX bytes:491259807 (468.5 MiB)  TX bytes:29316620 (27.9 MiB)
          Interrupt:23 

scott@scott-desktop:~$ 
 
```

---

### Post by PilotJLR on 2007-08-11
Very good; the original addresses you chose are fine.
So then, desktop eth0 is 192.168.0.1 255.255.255.0, and the laptop's eth0 is 192.168.0.2 255.255.255.0, gateway 192.168.0.1

With this addressing, and with both interfaces up, see if the LAPTOP can ping 192.168.0.1

If this fails, then make sure you're using a crossover network cable and NOT a straight-through cable.

---

### Post by skymera on 2007-08-11
ok using my ethernet cable i borrwoed from my mum..

i cant ping my desktop :(

do i need a crossover cable?

---

### Post by PilotJLR on 2007-08-11
Yep - the configuration we've done (including turning on ip_forward) is good...

But you can't connect 2 hosts together unless you have a crossover cable. It's basically the exact same thing you have now, except a wire pair is reversed to allow host-to-host connectivity.
If you have a spare switch and extra network cable available, then that would also work too.

---

### Post by skymera on 2007-08-11
i have 2 ethernets.
thats it so far.

any use?

---

### Post by PilotJLR on 2007-08-11
2 straight-thru ethernet cables? No use for this purpose, unfortunately.

Once you get either a switch or 1 crossover cable, verify the laptop-desktop ping works, and then there will be 1 more step to get to the internet.
Basically just need to turn on IP masquerading as well, but that is just one more command.

---

### Post by skymera on 2007-08-11
thnaks for all tge help :)
you should visit more often,
well i better go...

2 50am lol

thanks again.

Sky

---

### Post by wirelessmonkey on 2007-08-11
Unless your network ports are auto-sensing, which I'm doubting, you do need a crossover cable to directly connect the laptop and the pc.

---

### Post by skymera on 2007-08-12
does firestarter play any role in this?

---

### Post by matburton on 2007-08-12
Yeh I would have suggested firestarter.
It works great as a bridge and is much easier to set-up, no command line work necessary!
I use it to bridge the wireless connection from my laptop to my xbox media centre.

---

### Post by skymera on 2007-08-12
so what would i have to do in firestarter?
after what should i do with my Desktop wired settings?
and laptop wired settings..?

i saw a crossover cable in Argos today. it was £10.
i was going to buy it but i thought i try other things first.

---

### Post by skymera on 2007-08-12
any help?
no matter how small, i appreciate it :D

---

### Post by skymera on 2007-08-12
someone?
im having doubts now..:(

---

### Post by nickpaton on 2007-08-12
Suggest disabling firestarter - having it enabled can often cause networking issues.

It's a good idea to then learn how to set it up once your network works though - I'm sure there are plenty of How To's around.

Good luck!

---

### Post by PilotJLR on 2007-08-12
Firewall doesn't have anything to do with this UNLESS it has been explicitly configured to drop or reject ICMP. I'm referring to the failure for the laptop to ping the desktop's eth0 interface.

Seriously... need to look at that cable. If you don't believe me, read this:
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by skymera on 2007-08-12
indeed. i have to pick one of those up :)
thans :D

---

### Post by nickpaton on 2007-08-13
100% agree Pilot - should have said that in my first - apologies - my stoopud!

Just mentioned the firewall bit to also make sure that it doesn't prevent connection, but as you say it shouldn't do.

Xover cables in UK:

If you want to send off - try [Ebuyer]("http://www.ebuyer.com/UK/cat/Cables-and-Tools/subcat/Crossover")

From [Argos]("http://www.argos.co.uk/static/Product/partNumber/6766654/Trail/C%24cip%3D1500006463.Office%2C%2BPC%2Band%2Bphones%3EC%24Brand%3DBelkin.Belkin%3EC%24cip%3D1500006487.PC%2Bconsumables%2C%2Bsoftware%2Band%2Bessentials.htm") (just to confirm the cable you were looking at)

From Maplins (if you have one in your area)  code A36AW thru A43AW depending on length.

[This]("http://www.maplin.co.uk/Module.aspx?ModuleNo=47616&&source=14&doy=13m8") page has some details.

HTH!

---

