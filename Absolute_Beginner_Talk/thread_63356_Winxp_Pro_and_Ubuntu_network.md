---
title: "Winxp Pro and Ubuntu network"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by MalcolmSex on 2005-09-07
I installed ubuntu last night and everything went perfectly but I've come up against a few problems.

I have a Winxp box set up for internet connection sharing and this is connected to the internet via a Zoom Adsl Modem. The Winxp box is also connected to the Ubuntu box via a crossover cable.

Now, I can share files across the crossover cable but I can't connect to the internet from the Ubuntu box via the WinXp box. I think this is due to port 80 being closed as I've checked the open ports on 192.68.0.1 which is my xp box and port 80 isn't on the list.

If anyone could help me I would appreciate it.

Oh and Hi :grin:

---

### Post by KingBahamut on 2005-09-07
Hmmm...interesting username. 

Whats the output of an 

sudo ifconfig 

are you actually getting an address from your XP box.

---

### Post by MalcolmSex on 2005-09-07
```
eth0      Link encap:Ethernet  HWaddr 00:30:BD:07:34:6B
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2002:55d2:94c0:8:230:bdff:fe07:346b/64 Scope:Global
          inet6 addr: fec0::8:230:bdff:fe07:346b/64 Scope:Site
          inet6 addr: fe80::230:bdff:fe07:346b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82705 errors:2 dropped:0 overruns:0 frame:0
          TX packets:79607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:18 txqueuelen:1000
          RX bytes:18824675 (17.9 MiB)  TX bytes:6845305 (6.5 MiB)
          Interrupt:11 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11992934 (11.4 MiB)  TX bytes:11992934 (11.4 MiB)
```

Cheers for any help. :)

---

### Post by Muhammad on 2005-09-07
Nice offending username you got there :D

That's odd, have you tried downloading all the updates from the Ubuntu Update Manager?

---

### Post by MalcolmSex on 2005-09-07
[QUOTE=Muhammad]Nice offending username you got there :D

That's odd, have you tried downloading all the updates from the Ubuntu Update Manager?[/QUOTE]

Yeah the user name is pretty wierd!

I've tried downloading the updates but it says there aren't any. That might be because I can't access port 80 though...

---

### Post by Nequeo on 2005-09-07
[QUOTE=MalcolmSex]Yeah the user name is pretty wierd!

I've tried downloading the updates but it says there aren't any. That might be because I can't access port 80 though...[/QUOTE]
 Hey there.

Could you also please type 'route' into the command line of your Ubuntu box and post the output? If I recall, Windows ICS sets your LAN IP address to 192.168.0.1. We need to make sure that address is configured as the gateway on the Ubuntu computer. 

If you want to test whether port 80 being blocked is the problem (though I highly doubt it - Windows XP Firewall ain't that tight... On my girlfriend's laptop I was happily ftping stuff around for a good 10 minutes before the firewall 'noticed' and popped up the 'block/unblock' application box), try temporarily disabling the Windows XP firewall.

It's just a shame so many ISPs try to make a profit by shipping cheap and nasty USB ADSL modems for the same price, if not more, as a quality ADSL router. 

Cheers,

---

### Post by MalcolmSex on 2005-09-07
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         BRIAN           0.0.0.0         UG    0      0        0 eth0
```

hopefully this will help

cheers

---

### Post by Nequeo on 2005-09-07
[QUOTE=MalcolmSex]```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         BRIAN           0.0.0.0         UG    0      0        0 eth0
```

hopefully this will help

cheers[/QUOTE]
 Okay... try this. In the terminal, type

> 
sudo route add default gw 192.168.0.1

And see if that works. When it asks for a password, enter your own.

We're basically telling the Ubuntu computer that if it needs to access the internet, it has to send its requests through your Windows XP machine. Of course, there is a way to do this graphically, but copy/pasting one line of text is a lot faster than clicking on a whole bunch of buttons!

Let me know what happens. If it works, you should be able to access the 'net immediately.

EDIT: Actually - it may not work afterall. Try it anyway - but I'm guessing your XP machine is called 'BRIAN'? If so, it may not be the route that's the problem, but maybe something else like the DNS settings...

Anyway, let me know if it doesn't work and we'll go from there.

---

### Post by MalcolmSex on 2005-09-07
I've typed in what you said and it doesn't seem to have worked. 

Yeah the Xp machine is called BRIAN!

---

### Post by Nequeo on 2005-09-07
[QUOTE=MalcolmSex]I've typed in what you said and it doesn't seem to have worked. 

Yeah the Xp machine is called BRIAN![/QUOTE]
 Okay then... Next thing we need to is to see whether it's a DNS problem. Try typing this on the Ubuntu machine:
> 
ping -c4 66.102.7.104

and post the result.

Then disable the Windows XP firewall and try it again.

---

### Post by MalcolmSex on 2005-09-07
I've just tried what you've suggested and found out it was Zone alarm blocking the internet! even though I've forwarded the network and I tried disabling it earlier.

Thanks for all the help :smile:  now I've just got to configure Zone Alarm properly. :???:

---

### Post by KingBahamut on 2005-09-07
Malcom, you can pick up a Linksys WRT54g now for close to inexpensive, that would cure most of your problems methinks.

---

