---
title: "No internet, works fine with LiveCD"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by ChrisA on 2006-10-20
Hi all,

I hope somebody can come up with a suggestion because I've no idea what's causing this.

When I ran Ubuntu from the LiveCD, everything was autodetected, including my ethernet adapter and I was happily surfing the web.

Now I've installed it to the HDD, I can't connect to the net. Everything in the network options looks fine to me (bear in mind this is my first day using Linux).

I'm connected to the net via a router through the LAN, I'm connected fine with this PC on winxp, just not with the installed Ubuntu. *confused*

Any help is appreciated. :)

EDIT: Forgot to add, using Dapper.

---

### Post by doobit on 2006-10-20
That's a little strange because the install should be the same as the live CD. You will have to do a little troubleshooting to find out why. First open a terminal and type ifconfig then tell us what that says. 
Also, is your router set for DHCP, or static IP?

---

### Post by ChrisA on 2006-10-20
Thanks for the reply.

Here's what I get:

eth0 
Link encap: Ethernet HWaddr 00:17:31:36:17
inet6 addr:fe80::217:31ff:fe31:2617/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:1 errors:0 dropped:0 overruns:0 frame:0
TX Packets:1 errors:3 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:60 (60.0 b) TX byes: 342 (342.0 b)
Interrupt:11 Base address: 0xf400

lo
Link encap: Local loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/28 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:7 errors:0 dropped:0 overruns:0 frame:0
TX Packets:7 errors:0 dropped:0 overruns:0 carrier:0
collision:0 txqueuelen:0
RX bytes:372 (372.0 b) TX bytes:372 (372.0 b)

EDIT: and router is DHCP

---

### Post by XaZuRy on 2006-10-20
I was experiencing the same problem once, the problem was that I didn't receive and IP adress from the DHCP server, and I can see that you don't receive one either. I don't know how to "fix" this problem, but a tempoary solution would be to manually configure your settings, that worked for me.

If you don't know how to configure it, do an ifconfig from your live CD or an ipconfig from your Windows partition (and show us the results), then I'll tell you what to "type in".

---

### Post by ChrisA on 2006-10-20
When you say manually enter the details, do you mean change the ethernet properties from DHCP to Static IP?

So I'd enter the IP address, subnet mask and gateway IP that the router gives me?

---

### Post by deadgobby on 2006-10-20
Ubuntu does not make it easy to use static DNS servers while using DHCP
 here is ubies wiki site link if the above statment
[https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dhcp%29](https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dhcp%29)
[http://sourceforge.net/projects/dad](http://sourceforge.net/projects/dad)
Gobby

---

### Post by Bachstelze on 2006-10-20
**ChrisA**, what if you just do :

```
sudo ifup eth0
```

---

### Post by jcrnan on 2006-10-20
I had a similar problem once. A sudo apt-get dist-upgrade fixed it tough :)

---

### Post by XaZuRy on 2006-10-20
#5 Yes, that's what I meant, but you should probably follow some of the other advice you've just been given.

---

### Post by ChrisA on 2006-10-20
Okay, thanks for the replies so far.

Using Static IP and entering the details in manually doesn't seem to work.

"sudo ifup eth0" returns-

Network unreachable, failed to bring up eth0. (in Static IP mode)
Interface eth0 is already configured. (In DHCP mode)

I'll try apt-get dist-upgrade now.

---

### Post by Bachstelze on 2006-10-20
Sorry, my mistake, you have to run this before :

```
sudo ifdown eth0
```

---

### Post by XaZuRy on 2006-10-20
Are you sure you configured it correctly?

---

### Post by ChrisA on 2006-10-20
ifdown eth0 followed by ifup eth0:

```
Listening on LPF/eth0/00:17:31:31:36:17
Sending on LPF/eth0/00:17:31:31:36:17
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11

No DHCPOFFFERS recieved
No working leases in persistent database - sleeping.
```

---

### Post by ChrisA on 2006-10-20
> **XaZuRy said:**
> Are you sure you configured it correctly?

Configured as in entering the IP/Subnet/Gateway correctly? Yes.

> **jcrnan said:**
> I had a similar problem once. A sudo apt-get dist-upgrade fixed it tough :)

I don't understand how that would work because I have no internet connection so it wont be able to apt-get the files? Excuse me if I'm talking nonsense!

---

### Post by Bachstelze on 2006-10-20
Well, it doesn't seem to be, since it still waits for DHCP offers... Please paste your /etc/network/interfaces file :)

---

### Post by ChrisA on 2006-10-20
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

etc...
``` on DHCP mode, or

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 82.2.85.183
netmask 255.255.255.0
gateway 62.253.189.143

auto eth1
iface eth1 inet dhcp

etc...
``` if I change it to Static IP, but surely it doesn't need to listen to DHCP offers if it's in Static mode?

---

### Post by Bachstelze on 2006-10-20
If it listens to DHCP offers, that means it is **not** configured in static mode. Are you pretty sure your file is the second version when you run ifdown && ifup ? Don't forget to save it ;)

Oh and by the way, when you're asked to paste some files, you should paste the whole of them, not just a few lines ;)

---

### Post by ChrisA on 2006-10-20
Okay, my interfaces file is the 2nd version from above. This is what I get for the ifdown + ifup:

ifdown:
```
ifdown: interface eth0 not configured
```

ifup:
```
SIOCADDRT: Network is unreachable
failed to bring up eth0
```

Sorry, but the Ubuntu PC and this WinXP PC are seperate, there is nothing else installed on the Ubuntu PC so I'm having to manually type it out here each time, hence cutting some things short. ;)

---

### Post by ChrisA on 2006-10-20
*bump*

Anyone?

If only I knew my way around a bit more I'd be able to figure it out myself. I'm just so lost at the moment. :(

---

### Post by jcrnan on 2006-10-20
I used a temporary wired nect acsess to do the dist-upgrade.

Btw: if that doesnt work you can try out the new Edgy eft. It fixed some wireless problems on my little sister pc. 

If neither work try out the nidswrapper instructions on [www.ubuntuguides.org](www.ubuntuguides.org)

---

### Post by wilberfan on 2006-10-21
I had this exact problem (still do, everytime I reinstall Dapper!) and this fixes the problem every time:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

I do NOT have a "Davicom" adapter (it's a D-Link), but this still works!  :cool:

---

