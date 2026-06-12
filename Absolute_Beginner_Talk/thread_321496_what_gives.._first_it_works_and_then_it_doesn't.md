---
title: "what gives.. first it works and then it doesn't"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by mosedavid on 2006-12-19
my wireless pci card (ra2500) was working perfectly.  I then disabled it in system/administration/network so that i could try to get my wired eth0 to work - i was pretty sure the hardware was broken but wanted to try.

Having realised that eth0 couldn't work i then enabled the wireless again.  Now it can't get an ip address from the dhcp server.  It was showing excellent signal strengh, I rebooted and now it shows no signal.  It's also sending out loads of packets - more than before.  

Every time i look in 'network' the wired eth0 is ticked where it says 'enable this connection' - i untick it, click ok, go out, go into it again and its enabled again.

totally confused... what the..:( :( :( :(  is going on?

---

### Post by tweedledee on 2006-12-20
> **mosedavid said:**
> my wireless pci card (ra2500) was working perfectly.  I then disabled it in system/administration/network so that i could try to get my wired eth0 to work - i was pretty sure the hardware was broken but wanted to try.

Having realised that eth0 couldn't work i then enabled the wireless again.  Now it can't get an ip address from the dhcp server.  It was showing excellent signal strengh, I rebooted and now it shows no signal.  It's also sending out loads of packets - more than before.  

Every time i look in 'network' the wired eth0 is ticked where it says 'enable this connection' - i untick it, click ok, go out, go into it again and its enabled again.

totally confused... what the..:( :( :( :(  is going on?

Try this in a terminal:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
sudo gedit /etc/network/interfaces
```
(Substitute your favorite editor for gedit if desired.)

In the file delete all but these lines (deleting these two lines, usually the first, will cause major problems):
```
auto lo
iface lo inet loopback
```

Then I suggest rebooting, as I've found that to be the only way to clear my (somewhat similar) network problems in Edgy, although in principle this should work:
```
sudo /etc/init.d/networking restart
```

You should then be able to configure your devices again.

---

### Post by mosedavid on 2006-12-20
tried your solution - sorry didn't work

its showing as connected but i cant ping out.  Basically the DHCP isnt working.  The other computers on the network can get to the router though and recieve their ip numbers.

the only network cards in the 'interfaces file ' are the loopback and ra0

...

i face ra0 inet dhcp
wireless-essid *******
wireless-key *************

auto ra0

---

### Post by mosedavid on 2006-12-20
to add.. i did - lwlist ra0 scan - this showed both my wireless hub and someone elses nearby so it must work to some extent.

it also showed up under iwconfig.  I put in 'ifdown ra0' - that returned 'network unreachable.  I tried 'ifup ra0' - that searched for dhcp on subnet 255.255.255.255 and returned no dhcp offers on port 67 - my network subnet is 255.255.255.0

---

### Post by tweedledee on 2006-12-21
> **mosedavid said:**
> to add.. i did - lwlist ra0 scan - this showed both my wireless hub and someone elses nearby so it must work to some extent.

it also showed up under iwconfig.  I put in 'ifdown ra0' - that returned 'network unreachable.  I tried 'ifup ra0' - that searched for dhcp on subnet 255.255.255.255 and returned no dhcp offers on port 67 - my network subnet is 255.255.255.0

A non-ideal solution that sometimes work is to assign to choose a valid static IP instead of relying on DHCP for assignment.  I've found with some wireless cards this is the only way I can get a reliable connection.  Oddly enough, sometimes after assigning a static IP and connecting once, DHCP will then work.  If that happens, I've found that the problem is sometimes in /etc/resolv.conf.  You can actually try this first if you want:
```
sudo gedit /etc/resolv.conf
``` and add the following lines to the end:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Those lines add the opendns servers; for some reason I've found that often helps for an initial DHCP connection (especially if you have switched between network cards).  If that solution works, you'll need to install (apt-get) resolvconf, then (sudo) edit /etc/resolvconf/resolv.conf.d/head to add the same 2 lines (which just ensures those 2 lines are always in resolv.conf instead of being overwritten periodically).  In your case, since you don't seem to plan on switching your activate card again, a single edit of resolv.conf may solve the problem.

If none of that works, I think you've exhausted my ability to help.

---

