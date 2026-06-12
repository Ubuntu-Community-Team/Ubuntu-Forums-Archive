---
title: "Wireless LAN doesn't work"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by GoUbuntu on 2005-12-03
This is my first attempt using any sort of Linux.

I've got a wireless LAN PCI card with RT2400 chipset.

I tried to set it up using System->Administration->Networking.  It appears in the  list with (ra0) in brackets.  In the properties I entered the SSID, set the key to be Hexadecimal and entered the 128 bit key.  I also set it to DHCP.  Out of that screen I clicked "Activate".

If I go to Network Tools, the default interface that it comes up with is Loopback interface.  "Unknown Interface (ra0)" appears in the drop-down list.  When I select "Unknown Interface (ra0)", there is an entry for IPv6 but no IPv4.  All the stats down the bottom (like physical address etc) are unavailable.

If I change from DHCP to manual configuration, and put in the default gateway etc, then in Network Tools, there is a line for IPv4 and the physical address and wireless speed etc are shown, but I can't ping the gateway.  It times out on the ping.  If I set it to DHCP, the ping doesn't even start.

The NIC card seems to appear correctly when I do "lspci | grep RaLink"

Where do I go from here?

BTW, the card works OK in windows.  I'm posting this from my windows boot up on the same PC.

Thanks for your help,
Brendon

---

### Post by GoUbuntu on 2005-12-03
OK, it's working now.  I didn't change anything, maybe it just needed me to reboot after changing it back to manual, then back to DHCP.

Edit: Oops, I spoke too soon.  It went a couple of times, continuously for a few hours, but then when I turned the computer on the day after, it didn't work.

I've tried sudo dhclient ra0, but it doesn't get any response.

Any ideas?


Thanks,

Brendon

---

### Post by GoUbuntu on 2005-12-07
Do I need to install a new driver?  It has worked before, so I'm not sure that I do.

Brendon

---

### Post by thenoobest1 on 2005-12-07
Im having the same problem on my parents computer, as a temporary fix (until i feel like messin with it again) i just restart the computer and it works fine.

what type of card are you using?

Maybe ndiswrapper will help?

[http://www.ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122](http://www.ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122)

good luck

---

