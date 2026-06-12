---
title: "iBook - Edgy Eft - Wireless"
date: 2006-10-07
forum: Apple PPC Users
---

### Post by Jose R on 2006-10-07
Installed 6.10 Beta yesterday.  Things went well, ethernet and wireless worked after a little bit of work in Network Manager.  Using a 14 iBook with a pre-extreme card and older airport.

But, I turned on the iBook today and Ubuntu no longer recognizes my wireless network.  The is what I get:

[CENTER]
 [IMG]http://www.fototime.com/B938B927D2C2F6C/orig.png[/IMG]
[/CENTER]

I'm a little confused?  It seems to recognize the card, but can't gain access to the airport.  Network Manager is no help since it doesn't see any wireless networks.

I'm guessing its a driver issue?  kernel?  Been searching the forums and other sites for help, but it seems most of the focus is on the extreme cards.

Do I need to do a full re-install of Ubuntu?  Or do I just need to find the right driver or kernel and install it?

Using WEP 128bit.  Wireless works fine on my iMac and when I boot into OSX on the iBook.

Many thanks in advance.

Jose

BTW, completely new to Linux and command line.

---

### Post by ssam on 2006-10-07
could it be [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63989)

in the kernel the prism2 driver has recently been re-enable, and is grabbing your wireless card before the orinoco driver can.

try running the commands
```
sudo modprobe -r orinoco_pci
sudo modprobe -r hostap_pci
sudo modprobe -r prism2_pci
sudo modprobe orinoco_pci

```

a quick fix is to black list the prism2 driver

to the file /etc/modprobe.d/blacklist

add the line
```
blacklist prism2_pci
```

and reboot

---

### Post by Jose R on 2006-10-07
ok, blacklisted prism2_pci:

[CENTER]
[IMG]http://www.fototime.com/E95BB7B7BEFE1BC/orig.png[/IMG][/CENTER]

That seem to work in recognizing my wireless network:

[CENTER][IMG]http://www.fototime.com/AB3186624C29F05/orig.png[/IMG][/CENTER]

Here is the iwconfig:

[CENTER]
[IMG]http://www.fototime.com/58F5354787EB228/orig.png[/IMG][/CENTER]

And my network interfaces:

[CENTER]
[IMG]http://www.fototime.com/BF86622FDA65EA5/orig.png[/IMG][/CENTER]

But, still no luck in having Network Manager acknowledge my wireless network.

But, I'm connected by wireless through wifiradar.

I still need to get the nm applet to work properly though.  It tells me there is no network connection.

Anymore ideas...thanks!

---

### Post by stmiller on 2006-10-07
To use network manager, you must have no additional entries in the /etc/network/interfaces file.

Just this inital entry:

auto lo
iface lo inet loopback


ONLY. NM creates its own config files for itself on the fly.

---

### Post by Jose R on 2006-10-07
Sweet!

That worked.

thanks/

---

### Post by prince_niceguy on 2006-11-01
> **stmiller said:**
> To use network manager, you must have no additional entries in the /etc/network/interfaces file.

Just this inital entry:

auto lo
iface lo inet loopback


ONLY. NM creates its own config files for itself on the fly.

that worked for me too... thanks a ton...:)

---

### Post by brenx on 2006-11-03
same problem with pre-extreme airport, but blacklisting prism2_pci does not help. 
wifi-radar shows no network, Network-manager can not connect to wireless network.

I tried all steps written above.

---

### Post by trash on 2007-03-18
> **brenx said:**
> same problem with pre-extreme airport, but blacklisting prism2_pci does not help. 
wifi-radar shows no network, Network-manager can not connect to wireless network.

I tried all steps written above.

I see this is an old thread but the issues seem to still exist in Feisty...

On a fresh install of feist my card and wireless worked flawlessly, after rebooting the problems began.. after trying the above fixes wireless worked flawlessly but again after a reboot I can't connect... does anybody out there have a real fix for g3 ibook cards?

EDIT: after doing a fresh install of Feisty wireless on G3 ibook is no problem, I am guessing maybe there was a problem with the dist-upgrade from Edgy to Feisty that caused problems... for me anyway.

---

### Post by Cannaregio on 2007-03-24
Feisty has solved the prism problem I had with the wireless of the kids' box.

Infamous INTERSIL ISL3890 Prism duette WN4201b ACCTON

I had tried everything to have it working, before feisty: all kind of drivers and madwifis for edgy, and then even other distros: bianca, sabayon, suse...

apparently some prism cards (made in taiwan) like the one that my kids unfortunately had in their box didn't work without windoze.
i was thinking to change the hardware wifi card in order to have it working

then came out the feisty fawn... everything works.

---

