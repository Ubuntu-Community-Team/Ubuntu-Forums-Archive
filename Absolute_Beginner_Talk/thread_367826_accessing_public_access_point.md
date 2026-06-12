---
title: "accessing public access point"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-02-22
At some point I lost the use of iwscan in the newest release of Ubuntu. I have tried repeatedly to log on to the city's public access point, so I tried to log on from command line but that isn't working either. Did the latest release get rid of the ability to access a wireless network with command lines? I had been able to connect to my wireless router but cannot seem to access the city site.
thank you, Tim

---

### Post by annda on 2007-02-22
i must say i'm not familiar with iwscan, but 
```
iwlist eth1(substitute your wireless interface) scan
```
gives the list of available APs. then can i go ahead with iwconfig to supply login info.

i don't know if that helps.

---

### Post by jordanmthomas on 2007-02-22
```
sudo iwconfig eth*whatever* essid *networkname*
```
You may need to do this after connecting.  Sometimes my Arch Linux box doesn't want to play nice so I have to
```
sudo dhclient eth*whatever*
```

---

### Post by SVWander on 2007-02-22
Okay, I was able to use the commands to scan for the network and that I could put in the proper data into iwconfig and tried to connect with dhclient but it came back with an error message:
NO DHCPOFFER received
No working lease in persistent database - sleeping
so I found the information but just like with wireless assistant I cannot connect. Do you have any ideas what could be wrong or rather what I AM DOING WRONG?
tim

---

### Post by Bachstelze on 2007-02-22
Problem : Your computer coult not get any DHCP offers.

Cause : There can be many. You have mistyped the ESSID, your router doesn't use DHCP, your router does use DHCP but for some reason is refusing the connection, your AP is out of range...

---

### Post by SVWander on 2007-02-22
> **HymnToLife said:**
> Problem : Your computer coult not get any DHCP offers.

Cause : There can be many. You have mistyped the ESSID, your router doesn't use DHCP, your router does use DHCP but for some reason is refusing the connection, your AP is out of range...

Like your avatar! Well, don't think I mistyped the essid. this is not my router but an access point run by the city. So it might be that the city doesn't use DHCP but they invite people to connect and I know many that have. Of course with a windows machine you would never know about such things as DHCP. There are instructions that I studied at the city's website. Oh and I am getting a pretty good signal.

---

### Post by po0f on 2007-02-22
SVWander,

The easiest way would probably be to use NetworkManager.  Open up /etc/network/interfaces and comment all the lines except "auto lo" and "iface lo inet loopback".  Restart the networking service by running `sudo /etc/init.d/networking restart`.  If NetworkManager isn't started, try hitting Alt-F2 and run `nm-applet`.  You should be able to connect to open networks with no configuration now.

---

