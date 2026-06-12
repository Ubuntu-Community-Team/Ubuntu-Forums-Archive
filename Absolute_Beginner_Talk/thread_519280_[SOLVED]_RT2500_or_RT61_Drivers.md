---
title: "[SOLVED] RT2500 or RT61 Drivers"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-08-06
My results of lspci -v give me this:
Network controller: RaLink RT2561/RT61 802.11g PCI
Subsystem: Linksys WMP54G ver 4.1

So would i use the RT2500 Drivers as described here:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29)

Or the RT61 Drivers as described here:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29)

My card was recognized out of the box, as ra0, and works fine for regular internet usage, but i keep being informed that improper, broken, or old drivers could be the root of my horrible samba problems.
Im going to attempt to get the drivers as up to date and correct as possible, but am  very confused now as to wich ones to use

---

### Post by Zedd on 2007-08-06
What is the name of the card itself?

---

### Post by Nythain on 2007-08-06
wish i could tell ya... short of the fact that its a linksys wireless g pci adapter and the lspci output wich says its wmp54g ver. 4.1

---

### Post by Nythain on 2007-08-07
bump

---

### Post by Austin_KW on 2007-08-07
That should be the rt61 driver.

You probably want the latest serialmonkey legacy drivers (rt61 cvs tarball) from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

---

### Post by Nythain on 2007-08-07
thanks... gonna give it a try when i have a bit... hopefully it helps fix a few issues i've been having

---

### Post by WI_Mike on 2007-08-08
> **Nythain said:**
> bump


What are you bumping? This dude is asking for help with his network card!?

:confused:

---

### Post by Nythain on 2007-08-08
i was bumping my thread, but that was a couple days ago, and it was like a day after i had posted and it got burried ... i know this person is asking for help with a network card, this person is me... and as you can see, it was taken care of... wonder why you care what i bumped a day or two ago

---

