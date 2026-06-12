---
title: "[SOLVED] Network doesn't start at bootup"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-01-09
Greetings,
I have Ubuntu 7.04 (CLI) installed from the alternate cd, and I am using this as my server.
After I first installed everything, the network configuration was dhcp, but I can't have it dhcp because I will need to know what it's static IP is to connect to it.

So, I copied the static ip configuration from my computer, to the server to /etc/network/interfaces and then my static IP address works. However, it will not work without first running sudo ifup ath0

So that means, if I power on my headless server, I can't access it because the network won't start.

Here is what I pasted into my /etc/network/interfaces file:
```
iface ath0 inet static
address 192.168.0.70
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid default

```

Like I said, everything works perfectly if I run:
```
sudo ifup ath0
```

But otherwise, my network is not starting at bootup.

Any ideas or suggestions?
Dr Small

---

### Post by fychan on 2008-01-09
I had a similar problem brining my WiFi ntwork up after boot - it only came up after a modprobe ndiswrapper had been run.

Anyways, I found on a trawl thru Google a nice hack (technically, it's not the best way to do things but... :D ):

Simply add the commands you want to run after boot to the /etc/rc.local file before the "exit 0" line, so in your case it would then read:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifup ath0

exit 0

```

---

### Post by OffAxis on 2008-01-09
I think you can append the ifup command (or equivalent) into the interfaces file and have it work.

Something like:
> iface ath0 inet static
address 192.168.0.70
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid default
**pre-up ifconfig ath0 up**


I know some wireless cards had to be cycled down/up, down/up to work properly (back in the days of dapper - I don't know if it's still true)

---

### Post by bodhi.zazen on 2008-01-09
Beat out by fychan :lolflag:

/etc/rc.local is often overlooked, but is *the solution* for these types of problems.

---

### Post by OffAxis on 2008-01-09
By the way, you should be able to assign a static ip at the router based on the MAC of your headless machine.
That way you can have the machine thinking it's dhcp, but the router keeps assigning it the same address.

---

### Post by Dr Small on 2008-01-09
Thanks for the help guys :)
I tried adding **pre-up ifconfig ath0 up** to my interfaces, and rebooted, but it didn't have any effect on it, so then I tried adding **ifup ath0** to rc.local, and it worked perfectly!

Thanks for all the help :) Now I can connect to my server over ssh now :D

Dr Small

---

### Post by Megatog615 on 2008-03-18
The real way to do this without the rc.local hack is to put this at the bottom of /etc/network/interfaces:
```
auto ath0
```And it will connect on bootup. This also means it happens even before rc.local so other services that may need the network will be available quicker. You'll be able to ssh into your box while it's still booting up!

---

