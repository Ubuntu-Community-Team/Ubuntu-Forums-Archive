---
title: "DIsabled my wireless card, now it's gone forever?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Hraefn on 2007-03-11
Total Stoopid Noob Move here...

I don't even know why I did it, but I've been in the process of trying to get my wifi card working on a new installation of Ubuntu.  I've managed to get the driver files I need (thanks to madwifi), and managed to install the madwifi drivers.  Thing is, now I need to re-locate the card...

Does anyone in Know More Than I land have a clue as to how I would go about re-introducing my wifi card to my computer??

Ubuntu 6.10

When I scan for pnp devices, this is what I got concerning the card:

network:0 UNCLAIMED
                description: Ethernet controller
                product: AR5211 802.11ab NIC
                vendor: Atheros Communications, Inc.
                physical id: 4
                bus info: pci@02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:e8200000-e820ffff irq:10

Thanks Ever-so Much!
Hraefn

---

### Post by mozkaynak on 2007-03-11
to activate it goto system - administration - networking. enter your sudo password and then you can activate your wireless card again

---

### Post by Hraefn on 2007-03-11
yeah..should have made that clearer...I removed it from the lineup of available internet connections (ethernet, modem, wireless). Now, it's not even listed in that lineup anymore.

Thanks for the quick reply, though!

---

