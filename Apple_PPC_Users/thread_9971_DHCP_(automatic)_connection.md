---
title: "DHCP (automatic) connection"
date: 2005-01-03
forum: Apple PPC Users
---

### Post by Sorin Paliga on 2005-01-03
Autoamtic (DHCP) internet connection does not seem to work , even if via proxy there is no problem at all.
Any idea about how to make it work via dhcp? UBUNTU runs on a IBook G3, otherwise works fine.

---

### Post by tiiim on 2005-01-03
[QUOTE=Sorin Paliga]Autoamtic (DHCP) internet connection does not seem to work , even if via proxy there is no problem at all.
Any idea about how to make it work via dhcp? UBUNTU runs on a IBook G3, otherwise works fine.[/QUOTE]


Im assuming you have done it via the networking option under the GNOME menu COMPUTER -> System configuration -> networking. If not run it through there.

If not what are the signs and what make of router or are you networking via another computer? (anybody else please feel free to post and help im not the biggest expert in this area...just throwing ideas around)

---

### Post by Sorin Paliga on 2005-01-03
[QUOTE=tiiim]Im assuming you have done it via the networking option under the GNOME menu COMPUTER -> System configuration -> networking. If not run it through there.

If not what are the signs and what make of router or are you networking via another computer? (anybody else please feel free to post and help im not the biggest expert in this area...just throwing ideas around)[/QUOTE]

Details: iMac running 10.3.7 as SOHO router; two other macs (imac and ibook) connect through it, no problem; and a pc running win (no problem). There has never been any problem with various Linux distros connected in this way, Ubuntu is the first! Usually, all other distros tested (mainly on the pc, of course) connect without any other setting.
Note: the internet provider allows such connections (Bucharest, Romania), so I am fully OK.

---

### Post by tiiim on 2005-01-03
[QUOTE=Sorin Paliga]Details: iMac running 10.3.7 as SOHO router; two other macs (imac and ibook) connect through it, no problem; and a pc running win (no problem). There has never been any problem with various Linux distros connected in this way, Ubuntu is the first! Usually, all other distros tested (mainly on the pc, of course) connect without any other setting.
Note: the internet provider allows such connections (Bucharest, Romania), so I am fully OK.[/QUOTE]
 did you do the network option in Ubuntu? under the networking application? where you can add a new connection and make it DCHP?

---

### Post by cow_racer on 2005-01-03
I never got my ibook to work with DHCP.  I even tried Pupm, Dhcpd, and the default that came with Ubuntu.

---

### Post by Sorin Paliga on 2005-01-04
Well, I think this is a bug with Ubuntu, and the only Linux distro, which does not automatically connect via DHCP! Sorry to write this... Note that during installation, final phase, DHCP was correctly detected.

---

### Post by wallijonn on 2005-01-04
Did you Applications -> System Tools -> Network Tools ?
Can you ping your router? 
Is the Gateway IP address and mask set correctly?

---

### Post by Sorin Paliga on 2005-01-05
[QUOTE=wallijonn]Did you Applications -> System Tools -> Network Tools ?
Can you ping your router? 
Is the Gateway IP address and mask set correctly?[/QUOTE]

In the same, identical circumstances there is another iMac and a PC via the same router, an iMac G3 400. And there were at least 5 Linux distros installed in this environment, all were/are OK; all, but Ubuntu, automatically detected internet connection and the HP deskjet 970 cxi (this is another bug with Ubuntu, printer detection). So  I think there is a bug with Ubuntu, at least ppc version. Note that DHCP was correctly detected during installation, and was asked whether to download updates (said NO).
Generally speaking, I think Warty has some major problems related with hardware detection and configuration. Intel version does not mount floppy, does not detect mouse port etc. I think that these are real and important problems to be solved in Hedgehog.
In another location, with manual settings via proxy, all is OK, and apt-get works fine.

---

### Post by tiiim on 2005-01-05
[QUOTE=Sorin Paliga]In the same, identical circumstances there is another iMac and a PC via the same router, an iMac G3 400. And there were at least 5 Linux distros installed in this environment, all were/are OK; all, but Ubuntu, automatically detected internet connection and the HP deskjet 970 cxi (this is another bug with Ubuntu, printer detection). So  I think there is a bug with Ubuntu, at least ppc version. Note that DHCP was correctly detected during installation, and was asked whether to download updates (said NO).
Generally speaking, I think Warty has some major problems related with hardware detection and configuration. Intel version does not mount floppy, does not detect mouse port etc. I think that these are real and important problems to be solved in Hedgehog.
In another location, with manual settings via proxy, all is OK, and apt-get works fine.[/QUOTE]
 i had dchp working fine on PPC version though so i think it random but yeah could be a few bugs somewhere on certain hardware.

---

### Post by jshamlet on 2007-06-07
I'm having the same problem, but it doesn't appear to be the hardware. I originally installed Edgy , and my network connection worked just fine. It was only after the upgrade to feisty that I have to manually (every time) select the wired network.

Once I select the wired network, I get an IP address, and all is well - but shouldn't Ubuntu remember that setting? It looks like a bug that i have to change that setting after every boot.

Note, I didn't intentionally install network manager. I did a default install of Edgy, and then used the auto-upgrade to Feisty.

EDIT: As an oddity, the machine in question is a Powerbook G3 (lombard) using the onboard 10/100 wired ethernet port. I have another Powerbook (Pismo) that i upgraded in the same way, but with an airport card, and it is working fine.

---

