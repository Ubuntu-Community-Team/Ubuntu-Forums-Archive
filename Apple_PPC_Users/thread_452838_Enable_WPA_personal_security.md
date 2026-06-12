---
title: "Enable WPA personal security"
date: 2007-05-23
forum: Apple PPC Users
---

### Post by rogue6 on 2007-05-23
When choosing a wireless network
Under wireless security 
There are only wep options 
Anyone know how to enable wpa?

---

### Post by stmiller on 2007-05-23
WPA only works for Airport Extreme cards in Linux. The original airport card can only do WEP. It might be possible to compile the hermes driver from source and create a new airport driver that can do WPA...

---

### Post by r1chard on 2007-05-23
> **stmiller said:**
> WPA only works for Airport Extreme cards in Linux. The original airport card can only do WEP. It might be possible to compile the hermes driver from source and create a new airport driver that can do WPA...

OK, wanting the same thing, I noticed this problem a while ago installing on an old Powerbook G4 with an original Airport.

Do you know of a working solution for PPC / wifi / WPA-PSK using either a non-apple PCMCIA card adapter or a USB adapter? I guess probably this means something which uses completely open source drivers, since most binary blob drivers are for Intel chip-sets AFAIK.

Regards
Richard

---

### Post by stmiller on 2007-05-23
Yes the prism2 802.11g chipsets work well with Linux. There are some others, but I don't know them off hand. The PPC part is irrelevant for this sort of thing. Linux is linux. :) So as long as there is a driver for the chipset in the kernel, you are all set.

---

### Post by r1chard on 2007-05-24
> **stmiller said:**
> Yes the prism2 802.11g chipsets work well with Linux. There are some others, but I don't know them off hand. The PPC part is irrelevant for this sort of thing. Linux is linux. :) So as long as there is a driver for the chipset in the kernel, you are all set.

Thanks for that information. Does that mean the WPA-PSK functionality (in conjunction with wpa_suplicant) is related to the card (or it's firmware), or to the driver, or a bit of both?

Regards
Richard

---

### Post by woozyking on 2007-05-24
I think it's related to the router. If the router's using WPA (or even WPA2), then Ubuntu will detect it as WPA (or WPA2).

And I've noticed that Ubuntu can't really detect out the exact method when the router's set to use WEP, it will then have several choices, nasty.

---

### Post by stmiller on 2007-05-24
> **r1chard said:**
> Thanks for that information. Does that mean the WPA-PSK functionality (in conjunction with wpa_suplicant) is related to the card (or it's firmware), or to the driver, or a bit of both?

Regards
Richard

Both. Most modern wifi adapters can do WPA. Some of the older 802.11b ones cannot. So it depends on the particular chipset (most 802.11g are okay with WPA) and also depends on IF there is a Linux driver for that chipset in the kernel. (Most all popular ones DO have a Linux driver).

And the driver can suck. Ex: the original airport card for Macs can do WPA under OS X, but under Linux can only do WEP. :-(

Search the wireless section of this forum. Lots of recommendations and good info there.

Install the program hwinfo

sudo apt-get install hwinfo

then run hwinfo and it will tell you the wireless capabilities of your network cards, among other stuff.

---

