---
title: "BT Voyager 1065 Laptop Adapter 802.11g"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-24
After working out how to install the drivers and configuring the network for a Belkin F5D7050, my friend needs to install his (Title) BT card to Edgy, so what are the drivers for this particular card, and where can I download (link please), and then, will configuration be any different or can I do what I did with the Belkin stick?

Thanks,
Camz

---

### Post by tyres on 2007-03-24
Hi,

You need the HowTo at this link [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

---

### Post by camz on 2007-03-25
That is not the wireless card he has

---

### Post by camz on 2007-03-25
Where can i get the drivers for his particular (name in title) card?

---

### Post by ramzai on 2007-03-25
Use search

[http://ubuntuforums.org/showthread.php?t=371212](http://ubuntuforums.org/showthread.php?t=371212)

---

### Post by camz on 2007-03-25
I would prefer not to use ndiswrapper if possible, but if it's necessary I will, but is there any way I could just download the drivers like with my Belkin.

---

### Post by tyres on 2007-03-25
Hi,

It's not the brand of wireless card that is important, it's the chipset inside the wireless card.  If your friend does a 'lspci' he should see (probably the last entry) something like this;

02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Just for the record, I'm writing this on a laptop using a BT Voyager 1065 wireless adapter, set up using the HowTo I pointed you at.

To my knowledge there are no native Linux drivers for the BT 1065. BT doesn't 'do' Linux :-( ndiswrapper is your only recourse. But, hey, it works!

---

### Post by camz on 2007-03-26
Oh, but I installed ndiswrapper and did everything on that guide and it didnt work. and it is definately the rigt kind :(

---

### Post by tyres on 2007-03-26
Like I said, I'm using a BT Voyager 1065 adapter myself to send these messages. I used that HowTo to set it up, so it is the right driver for that adapter. The chances of two BT Voyager 1065 wireless adapters needing different drivers is pretty remote, I think.

What does the 'lspci' command show you? That will tell you what chipset your dealing with. If it says BCM4318 somwhere (as it should) then that HowTo tells you how to set up wireless cards with that chipset.

When you say it didn't work, what precisely does that mean? Do you get any kind of error message in the logs, does 'dmesg' say anything? Is everthing ok in the setup log for the script? You may need to poke around a bit to find the problem. 

For a start, does 'ndiswrapper -l ' show you that the driver is installed, and the hardware present?

---

### Post by camz on 2007-03-27
It's definately that chip, I will learn it and stamp this guide into my head, as I won't get another chance to get it working until Saturday.

---

### Post by tyres on 2007-03-27
I'd check the network interface configuration. If that's not right you may not get a light on the adapter even if the driver is working properly, and certainly won't get a connection.

Good luck.

---

