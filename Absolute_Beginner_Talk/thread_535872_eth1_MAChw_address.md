---
title: "eth1 MAC/hw address"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Fat Jonny on 2007-08-27
I've just installed Ubuntu 7.04 as a dual boot with my Vista system! I am brand new to Linux so have thrown myself into the deep end... Here is one problem I've looked for but can't seem to find the solution to!

My PC is connected to a cable modem, which seems to fix the connection based on the MAC/hardware address of the network card. When I boot into Vista and turn on the power to the modem, it creates a new connection. If I then reboot into Ubuntu, it doesn't connect. The only way to connect is to physically power off and on the modem and create a new connection each time I switch between OS's.

I found the MAC address of the connection in Vista, and this always stays the same. But every time I boot into Ubuntu the MAC address (as shown under eth1 in "sudo ifconfig") seems to change each time I boot. The only other way I can connect after rebooting into Ubuntu is to set the MAC address like this:

sudo ifconfig down
sudo ifconfig hw ether 00:11:22:33:44:55 (set to Vista MAC address)
sudo ifconfig up

I found something on the web that said I could just stick this into /etc/network/interfaces, but I can't figure out how or what format it should be in. This doesn't seem to work:

auto eth1
iface eth1 inet dhcp
hwaddress ether 00:11:22:33:44:55

I'm sure this is something simple.... any ideas? apart from buying a router of course!

---

### Post by wormser on 2007-08-27
It looks like you are on the right track according to this [guide]("http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/").  The last line is tabbed.  I am not sure if that is the problem, but give it a shot.

> Just add another line below it to make it look something like this:
```

auto eth0
iface eth0 inet dhcp
       hwaddress ether 01:02:03:04:05:06

```
Then restart your adapter
```

sudo /etc/init.d/networking restart

```


---

### Post by phyrewall on 2007-08-27
I know this isn't a "no cost" option, but if you're using a cable modem that locks onto MAC addresses, why not buy a decent router that is capable of cloning your PC's MAC address? That way you can reboot or add more devices to your network without having to restart the modem.

Just my $0.02

---

### Post by Fat Jonny on 2007-08-27
> **phyrewall said:**
> I know this isn't a "no cost" option, but if you're using a cable modem that locks onto MAC addresses, why not buy a decent router that is capable of cloning your PC's MAC address? That way you can reboot or add more devices to your network without having to restart the modem.

Just my $0.02
If I did buy a router I wouldn't need to clone the MAC address, since the modem isn't fixed to one specific MAC address, it just can't be used with two different mac addresses without powering off and on. So I'd just plug in the router and it would be ready to go, since the routers MAC address would be fixed... but since I only have one PC and have no plans to add more to the network, I'd rather just configure Ubuntu to use the same MAC address as Vista. I don't see the point in unnecessary hardware clogging up the underside of my desk...

But two things I don't understand are this:

1. I thought MAC addresses were hardware fixed, so the MAC address in Vista and Ubuntu should always be the same shouldn't it?

2. Why would the MAC address change every single time I reboot Ubuntu but stays fixd in Vista?

wormser, I'm at work at the mo, but will try adding a tab and see if that makes a difference.

---

### Post by Fat Jonny on 2007-08-27
Adding the tab didn't work.... anybody have any other ideas?

---

