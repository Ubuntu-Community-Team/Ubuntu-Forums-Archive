---
title: "Open Ports? Do I have a problem?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by CallMeDerek on 2007-04-03
I recently converted all my systems in my home network to Kubuntu 6.10 (except one running a windows shared domain for printing/files)

Once I got everything working I decided to wander over to GRC and run Shields Up from one of the Kubnutu boxes – to my surprise GRC is reporting a lot of open ports – in fact almost all of them.

I am not a networking guru, in fact I am constantly surprised I am able to get this stuff to work at all.  My understanding is that by default Kubuntu ships with all ports closed.

My questions are

- Is GRC Shields Up reporting on my Router or my workstation?  In other words just because the ports are accessible to the internet from the router does that translate to a risk to my workstations behind it?

- The IP Address that Shields UP displays is assigned to the Router (I assume) – I am using 192.168.0.xxx ip ranges for my internal DHCP range for the systems behind the firewall – if this is non routable is anything behind the firewall even accessible from the internet?

- Is there a better test out there that would be a better check of my security?

I know this is really open ended, simply looking for advice.

My setup is as follows:
WildBlue Internet Satellite Modem > 
     Netgear FR114p wired Router/Firewall<crossover> Linksys Wireless Router

Both Routers are running DHCP and both a have Firewall capability enabled (as far as I can tell) – there are no software firewalls installed on the Kubuntu boxes only on the one remaining windows box.

Thanks in advance!

---

### Post by jvc26 on 2007-04-03
Download firestarter, which is a GUI frontend to configure the inbuilt linux firewall, iptables:
```

sudo apt-get install firestarter

```
Run that to configure iptables (the inbuilt linux firewall) You can then try the shields up test again - iptables isnt configured by default, as a quick:
```

sudo iptables -L

```
will probably show you that there are no rules configured.
Il

---

### Post by H3g3m0n on 2007-04-03
GRC Shields up will report on whatever device is seen from the internet, if your router is the thing that has your external ip then this is the problem, not any of your computer systems.

Make sure that shields up is actually saying that the ports are open, from memory shields up complains if the ports respond at all, ie closed, filtered etc... Rather than completely stealthed. It's possible your router does something odd and is lying about what ports are open or Shields up is scanning a transparent proxy from your isp rather than your home system.

Might be worth trying a few other online port scanners such as [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by PriceChild on 2007-04-03
If you are using a router, then Shields Up is scanning your router.

None of your boxes will be reached unless you have configured "port forwarding" on the router.

I suggest you enable your router's firewall or close its ports to make yourself near invisible.

---

