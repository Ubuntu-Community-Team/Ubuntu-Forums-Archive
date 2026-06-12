---
title: "ndiswrapper -v"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by anfractuosities on 2007-10-15
ndiswrapper -v gives me this...i tries reinstalling but to no avail. i need help!!


modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

i dont know if its related, but i cant get a wlan0 or equalivent to show up in iwconfig

---

### Post by jingo811 on 2007-10-15
Do you know your wireless device's brand model and chipset?

---

### Post by anfractuosities on 2007-10-15
belkin f5d9010

in the device manager the vendor is

Atheros Communications, Inc

I'm not sure if that helps.  I also have an intel mini pci card that works but i need to send it in to get a replacemnt.


lspci shows this 

 Atheros Communications, Inc. Unknown device 0024 (rev 01)

---

### Post by jingo811 on 2007-10-15
I feel a little rusty in my Wireless skills so double check with me when you search for you main device in this database!
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

### Post by jingo811 on 2007-10-15
Belkin F5D9010 doesn't seem to be listed ndiswrapper is probably the correct method.
Is your Belkin a USB or PCI wireless?
You'll need to find your Belkin Wireless setup CD and find the driver folder that contains [COLOR="DarkOrange"]*.inf[/COLOR]  and [COLOR="#ff8c00"]*.sys[/COLOR] files!

---

### Post by anfractuosities on 2007-10-15
its not on that list, i guess, 

 i've been getting hung up in the same spots when trying to instal some "supported" usb wirless adapters. (which i returned

lshw -enable test

network UNCLAIMED
                description: Network controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: iomemory:ff7f0000-ff7fffff irq:10

---

### Post by jingo811 on 2007-10-15
Is number 35 the same wireless device as your own?
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

---

### Post by anfractuosities on 2007-10-15
yes, but i believe it is a differnt chipset.  When i installed the drivers suggested on that doc, the device was not recognized...

---

### Post by jingo811 on 2007-10-15
You know what this is over my head I'm just an apprentice :KS posing as a wizard.
Make a new thread in this sub-forum instead it's more appropriate and you'll get the true wizards to help you out!
**"Networking & Wireless"**
But before you post in there let them now this and "code" the outputs # icon to make things easier to read!

[COLOR="DarkRed"]1.[/COLOR]
Do these in terminal and show them the input and outputs.
```
$ lspci -nn
```
```
$ lshw -C network
```

[COLOR="#8b0000"]2.[/COLOR]
Tell them you didn't find your wireless device listed in this database.
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

[COLOR="#8b0000"]3.[/COLOR]
Tell them the ndiswrapper list doesn't seem to be correct with what you really have.
Number 35 is close but doesn't seem like what you have.
[http://ndiswrapper.sourceforge.net/j...,33/id,list_b/](http://ndiswrapper.sourceforge.net/j...,33/id,list_b/)


That should be a good start to make in the sub-forum called **"Networking & Wireless"** good luck Jim this tape will self destruct in 10 seconds..... :)
[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

---

### Post by anfractuosities on 2007-10-15
great thanks!

---

