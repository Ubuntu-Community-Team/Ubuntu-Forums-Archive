---
title: "Basic networking help needed"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by wooly on 2007-03-21
Hi,
I'm trying to network two Linux machines.

Computer #1 has Fedora 6, computer #2 (laptop) has Ubuntu Edgy.
They each have a network card, connected together via crossover cable.
Green LEDs on the NICs are lit up. Both have avahi daemon running.

"ifconfig" on #1 shows:
eth0 Link encap:Ethernet HWaddr 000:FE:03:27:47
inet addr:169.254.252.98 Bcast:169.254.255.255 Mask:255.255.0.0
inet6 addr: fe80::20f:feff:fe03:2747/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 etc...

"ifconfig" on #2 shows:
eth0 Link encap:Ethernet HWaddr 00:0F:59:34:8B:6A
inet addr:169.254.252.99 Bcast:169.254.255.255 Mask:255.255.0.0
inet6 addr: fe80::2d0:59ff:fe34:8b6a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 etc ...

I see this line in /var/log/messages on machine #1:
Mar 21 07:54:12 john named[2493]: listening on IPv4 interface eth0, 169.254.252.98#53

... So I think the network should work. But:

"ping 169.254.252.98 " from laptop #2 times out.
"ping 169.254.252.99" from computer #1 also times out.

I want to be able to move and copy files back and forth, and use the modem connection of #1 from either machine. 

I'm probably forgetting something obvious. Any advice will be much appreciated.

---

### Post by banditti on 2007-03-21
169. ip address means that it is probably setup as dhcp and there are no dhcp servers.   169 is not valid.  I would setup a static ip address for both.

---

### Post by sardion on 2007-03-21
You are connecting the computers to each other directly?

Normally, one places a router in between them which then also conencts to the internet.

If you really don't want to do it this way (or don't have a router and don't want to buy one even though they are cheap), you will have to configure one of the linux machines to act like a router.  This involves a lot of work, and I am not going to go into here in the beginner forum.

If you really want to try that, post in a more advanced section (I don't know enough to tel lyou all the howto anyways).  But I would suggest just using a router like more or less everyone else does.

---

### Post by wooly on 2007-03-21
> **banditti said:**
> 169. ip address means that it is probably setup as dhcp and there are no dhcp servers.   169 is not valid.  I would setup a static ip address for both.

Thanks, I'll try setting them both manually.
What is a typical ip address for this type of network?

I'm not using a router because my only internet access here is via dial-up.
The few routers that I've seen that allow dial-up seem to use it as a backup to broadband.

---

### Post by dfreer on 2007-03-21
[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

On a home network, it is generally best to use a the private IP Addresses. The article above has a list of private IP addresses, most people use the 192.168.0.XXX range. Your are right in that most routers do not have a modem connection, so the way you are doing things is probably best.

To set up static IP addresses (so that it will stay this way even after rebooting), edit your /etc/network/interfaces file on both machines:

```
## Example /etc/network/interfaces file
## You will want to edit this for your specific needs

# 10/100 Ethernet Card eth0
auto eth0
iface eth0 inet static
        address 192.168.X.Y         # X can be any number from 0-254, but it must be
                                    # the same across the entire network (both machines).
                                    # Y must be unique to each machine.
        netmask 255.255.255.0
        network 192.168.X.0         # must be the same as X above
        broadcast 192.168.X.255     # must be the same as X above
        gateway 192.168.X.Z         # Z should be the same as Computer #1's Y address
                                    # Assuming Computer 1 has the internet connection 
                                    # shared. That is another matter.

```

After a reboot (or a *sudo /etc/init.d/networking restart*), you should be able to share files (assuming you have Samba configured correctly) and internet connection sharing (assuming you have that configured correctly). I think firestarter has a internet connection sharing wizard, but I dunno how well it works. Good luck!

---

### Post by timcredible on 2007-03-21
your ip addresses are ok.  169.254.x.x is a private address range that's not routable on the internet, but you're not trying to use those addresses on the internet, so they're valid, no need to change them.  does one of the machines have a firewall running that prevents pings?  also, check to make sure your crossover cable is actually good and has the correct pinouts.  The reason you see those addresses on your home machines is that your dsl/cable modem converts those private addresses to a real address (nat).

---

### Post by wooly on 2007-03-21
> **dfreer said:**
> 

After a reboot (or a *sudo /etc/init.d/networking restart*), you should be able to share files (assuming you have Samba configured correctly) and internet connection sharing (assuming you have that configured correctly). I think firestarter has a internet connection sharing wizard, but I dunno how well it works. Good luck!

I was able to get ping working both ways, after changing to 192.168.x.x addresses and adding the ip address to /etc/hosts on machine #1 (not sure which change fixed it).

Thanks, everyone. I really appreciate your suggestions.

Dfreer, I was hoping to set up the 2-computer network without getting into Samba. Is it necessary?
What do you mean by internet connection sharing? is there a gui or config file for it?

---

