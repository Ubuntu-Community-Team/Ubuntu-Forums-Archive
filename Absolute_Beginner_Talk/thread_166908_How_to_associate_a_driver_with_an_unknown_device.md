---
title: "How to associate a driver with an unknown device?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by pshnfry on 2006-04-27
I'm working through various guidelines for installing a RT2500 based wireless PCI nic.  Support for this chipset is supposedly built into Breezy but I think the problem relates to the card being an unknown device.  

sudo lspci = 0000:00:09.0 Network controller: RaLink: Unknown device 0302

sudo lshw =
*-network:0 UNCLAIMED
             description: Network controller
             product: RaLink
             vendor: RaLink
             physical id: 9
             bus info: pci@00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:db000000-db007fff irq:10

sudo lsmod | grep rt2500 =
rt2500                149220  0

Any assistance appreciated.

Cheers,

Peter.

---

### Post by az on 2006-04-27
[QUOTE=pshnfry]I'm working through various guidelines for installing a RT2500 based wireless PCI nic.  Support for this chipset is supposedly built into Breezy but I think the problem relates to the card being an unknown device.  

sudo lspci = 0000:00:09.0 Network controller: RaLink: Unknown device 0302

sudo lshw =
*-network:0 UNCLAIMED
             description: Network controller
             product: RaLink
             vendor: RaLink
             physical id: 9
             bus info: pci@00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:db000000-db007fff irq:10

sudo lsmod | grep rt2500 =
rt2500                149220  0

Any assistance appreciated.

Cheers,

Peter.[/QUOTE]

The device has an id that is different from the ids in the linux driver.  See if a more recent version of the driver (like boot the Dapper live cd) supports more hardware.  If not, go upstream and see if the homepage for the Ralink linux driver has a list of supported id, and see if your's can be added.

You may have to hack the code (usually, one file contains all the pci ids - just add a line with your's) and recompile the driver to see if it actually works, of ir it's a revision of a chipset that needs more work than that.

---

### Post by pshnfry on 2006-04-28
Thanks for that, sorry I missed your reply last night (1:30am here and work the next day - the end of a long learning night!).

Are the pci id's in the info I supplied above for driver and hardware? I would like to be able to interpret rather than blindly follow, I have another wireless nic with Atheros chip I could look at, and I could look at other distro's as well if I know what part to look at.

Also, any tips on finding the file with pci id's?  And by recompile do you mean "make" or another process I'll need to look up?

The driver is the latest found through serial monkey and the specific card manufacturer and model number is listed as supported with a question mark so I doubt I'll have any joy with an updated driver. 

Cheers,

Peter.

---

### Post by az on 2006-04-28
The pci id that you see is the one for the hardware.

Your best bet is to take this upstream, to the developers of the linux driver.

---

### Post by pshnfry on 2006-04-28
I don't want to push my luck but I do want to understand.

Is 0302 the pci id?

Where do I see the relevant pci id's the linux driver?

---

### Post by az on 2006-04-28
Yes.  

Do you see your brand of card here?

[http://ralink.rapla.net/](http://ralink.rapla.net/)
[http://rt2x00.serialmonkey.com/wiki/index.php/Hardware](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware)


I looked quickly at the source code but could not find the file with the list of pci ids.  You should realy ask someone from that project.  They have a forum...
[http://rt2x00.serialmonkey.com/phpBB2/](http://rt2x00.serialmonkey.com/phpBB2/)

---

### Post by az on 2006-04-28
[QUOTE=pshnfry]I don't want to push my luck but I do want to understand.
[/QUOTE]

This is a forum.  You don't push your luck by asking questions.  I am sorry if I sometimes leave out details - I often get interrupted...

---

### Post by pshnfry on 2006-04-28
Thank you, all appreciated.

The hardware is listed in both links, by manufacturer not pci id.  I'll try that forum.

---

### Post by pshnfry on 2006-04-28
Contacted Serial Monkey forum support. The pci id (0302) indicates RT61 chipset, the manufacturer has changed the chipset at some point.  RT2X00 driver (under development and still unstable) is required which is currently "broke" and has not yet supported this chipset in practice although is meant to.

I'll swap cards for one of our other pc's and try Atheros chipset support.

Thanks for the help azz.

Cheers,

Peter.

---

### Post by Stone123 on 2006-04-28
[QUOTE=pshnfry]Contacted Serial Monkey forum support. The pci id (0302) indicates RT61 chipset, the manufacturer has changed the chipset at some point. 

Peter.[/QUOTE]
That card(i ment driver) is supported in dapper, all you need is firmware, search forums for howtos. And i think its ralink original .

---

### Post by az on 2006-04-28
[QUOTE=pshnfry]

I'll swap cards for one of our other pc's and try Atheros chipset support.
[/QUOTE]

You can just use ndiswrapper.

You don't even have to blacklist the linux driver since it isn't even being loaded.

---

