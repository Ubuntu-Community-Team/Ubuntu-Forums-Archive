---
title: "HELP experts my ancient computer"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Kn6QWT on 2006-09-08
-

---

### Post by lapsey on 2006-09-08
> **Kn6QWT said:**
> bestek 10/100m rtl 8139d realtek chipset lan card
motorola surfboard sb5101 cable modem
mydestiny cable internet

Apparently the sb5101 works fine when connected to the PC via the network card.

Does it have a web interface for setting up a cable internet connection? If connected by network cable (NOT USB!), try going to [http://192.168.10.1/](http://192.168.10.1/) in your web browser.

---

### Post by Huzudra on 2006-09-08
surfboard modems are 192.168.100.1, or atleast the one that the cableco provides for us is which i would imagine is similar to yours.

---

### Post by lapsey on 2006-09-08
If you can connect over the network cable to the modem then you are good to go. 

Linux has no difficulty with the network card you mentioned, so i think the only thing you need to do is change the network settings of your xubuntu installation (when you have it again that is). 

The most basic way to do this is to look for the file called 'interfaces' in /etc/network

edit the file so it looks like this:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.10.2
netmask 255.255.255.0
gateway 192.168.10.1


at my network, the gateway is 192.168.1.1 so i make the local address of my machine 192.168.1.2. you can have any number you want in fact, as long as the first 3 are the same throughout the network. 


BTW, until you are sure you can afford to lose windows, perhaps you would like to try Dual Booting (installing linux on a partition on the disk) instead? The option is there in the installation menu.

---

### Post by Kn6QWT on 2006-09-09
-

---

### Post by Huzudra on 2006-09-09
> **Kn6QWT said:**
> yes the modem's web interface is 192.168.100.1
and typing it at the address bar of firefox
results to "server not found"

additional info:
connection is dynamic ip
and there's no ip address

i want to get rid of windows and
i really like the whole ubuntu philosophy.
i use this computer plainly for internet
and it's not functioning.

have you tried power cycling the modem?  ocassionaly the internet here drops out and the only way to 'fix' it is to power cycle the modem (and router).  its caused by poor signal which is caused by poor running of the cable which was caused by poorly educated previous owners.](*,) 

if powercycling the modem does work take a look at the logs and at the signal page.  the downstream power level is a good snapshot of how shoddy the connection is.  you want it to be on the positive side of zero.  a good connection is greater than 6 iirc or maybe it was 20 and higher?  im a bit fuzzy on it.  our connection is bad, its -4!  the internet blinks on and off like a  set of traffic lights :(

---

### Post by Ozitraveller on 2006-09-09
1. Check out the links below
2. Xubuntu
3. UbuntuLite.org
4. Server install + Fluxbox, which is about the same as DSL
    [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)
5. Checkout DSL (DamnSmallLinux.org)

Also I think there are some Ubuntu people working on a lighter Xubuntu using Fluxbox 

I hope that helps

---

### Post by jimrz on 2006-09-09
you might consider picking up a 4-port + wlan router. they are pretty inexpensive anymore + most (netgear and linksys, for 2) will auto-configure themselves with your cable isp and ubuntu then needs only to find the router and does so easily (have setup several sysems this way with various netgear models with no issues at all). also, the router will provide your dhcp (while allowing the option to reserve a specific ip for a specific machine effectively giving  static ip while still using dhcp, handy if you use wireless / network-manager), and provide nat and various other services.

---

