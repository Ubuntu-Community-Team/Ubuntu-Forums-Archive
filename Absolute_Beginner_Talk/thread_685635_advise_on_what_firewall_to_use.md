---
title: "advise on what firewall to use"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by ryan73 on 2008-02-02
I have a couple P3 (350) laying around they only have 128 RAM and 10 gig hard drives. I would like to install a firewall with a GUI because I really don't know command line. I guess I could learn just for a firewall. The boxes have onboard nic and I know I would have to buy another PCI NIC.

I'm looking for a firewall with GUI that will work on old computers, that is easy to set up and will also work with xp.  Any advise?

---

### Post by njparton on 2008-02-02
Will you be running one of these as just purely a firewall?

Install webmin and you'll be able to administer it completely remotely via a browser including the inbuilt iptables firewall.

Firestarter is the gui for iptables but I've never had much success via that route.

You may also want to consider a specific distro for this purpose such as m0n0wall.

---

### Post by gn2 on 2008-02-02
Are you intending to use a P3 PC as a firewall? 
If so it will be a very expensive waste of electricity compared with using a router with it's own firewall.

---

### Post by ryan73 on 2008-02-02
yes it will be just a firewall nothing else.

---

### Post by Whiffle on 2008-02-02
> **gn2 said:**
> Are you intending to use a P3 PC as a firewall? 
If so it will be a very expensive waste of electricity compared with using a router with it's own firewall.

Agreed.  Unless you've got more uses for it than just a firewall, pick up a router with a firewall in it, it will pay for itself in electricity costs.

---

### Post by bumanie on 2008-02-02
I doubt you will get a firewall that will work on both linux and xp, as they use totally different file systems. The ones to try on ubuntu are firestarter or gurd dog, although most say firewalls aren't needed as all of ubuntu's ports are closed by default. With only 128 mb ram you should use xubuntu or fluxbox (I think it,s called - you may have to check that) and install via the alternate cd as 128 mb ram will probably not be able to run a live cd.

---

### Post by njparton on 2008-02-02
Good points, but you could also expend the P3 machine to act as a file server etc etc in the future.

If not, think of the planet and buy a router with a NAT and SPI firewall built in.

---

### Post by gn2 on 2008-02-02
> **njparton said:**
> you could also expend the P3 machine to act as a file server etc etc in the future.

Or get a Linksys NSLU2 Network Storage Link which uses much less power than a P3 PC.

---

### Post by njparton on 2008-02-03
Does that have a hardware firewall built in?

---

### Post by gn2 on 2008-02-03
My suggestion would be to use a router with firewall and an NSLU2 instead of running a P3 PC 24/7.

---

### Post by yaztromo on 2008-02-04
We used to use the Smoothwall linux distro on an old VIA-EPIA at home as a NAT router and iptables firewall. It's a small download and dead easy to install. It also has a web administration page so you can configure things like port forwarding etc from a browser on one of your XP machines.

Unfortunately Smoothwall is not easily expandable so now we use a Ubuntu Fiesty box with webmin and iptables. With this method you can also make it a file server, game server, or whatever.

If you definitely only need a firewall with NAT routing then forget Ubuntu and go with [Smoothwall]("http://www.smoothwall.org/")

---

### Post by max renn on 2008-02-04
Hey, that NSLU2 looks cool as heck!!!  You could put a firewall on it if you multihomed the nic or add a usb nic to it.  SWEET!  Thanks for the post :)

---

