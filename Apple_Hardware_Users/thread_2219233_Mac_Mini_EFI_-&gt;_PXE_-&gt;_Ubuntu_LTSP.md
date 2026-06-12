---
title: "Mac Mini EFI -&gt; PXE -&gt; Ubuntu LTSP?"
date: 2014-04-23
forum: Apple Hardware Users
---

### Post by charlieott on 2014-04-23
I recently set up an Ubuntu 12.04.4 LTSP Server. The LTSP documentation has been phenomenal and I have been able to do a lot of different tweaks to create solid thin clients that can be used for software development at my office.

However, I have been tasked with an assignment that has proven to be quite difficult. We have about 20 Apple Mac Minis.  These small PCs are packing 8GB of RAM with an Intel Core i5 and Intel HD 4000 Graphics. However, most of the engineers in the office do not like OS X.

My assignment is to get the Mac Minis to boot as thin clients for Ubuntu 12.04.4 LTSP. I have made some progress by doing the following:

Install a Mac OS Partition on a thumbdrive with rEFIt. [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
Place an MSDOS FAT partition on the same thumbdrive with iPXE. [http://ipxe.org/download](http://ipxe.org/download)

This actually allowed me to utilize the rEFIt bootloader and start the SYSLINUX image pointing at the iPXE kernel.

However, no network card was found.

So I got the Device and Vendor ID from the Broadcom 57766-A1:
Vendor ID:    0x14e4
Device ID:    0x1686

And added it to the file: /ipxe/src/drivers/net/tg3/tg3.c

Which looks something like this:

static struct pci_device_id tg3_nics[] = {
PCI_ROM(0x14e4, 0x1644, "14e4-1644", "14e4-1644", 0),
PCI_ROM(0x14e4, 0x1645, "14e4-1645", "14e4-1645", 0),
PCI_ROM(0x14e4, 0x1646, "14e4-1646", "14e4-1646", 0),
PCI_ROM(0x14e4, 0x1647, "14e4-1647", "14e4-1647", 0),
PCI_ROM(0x14e4, 0x1648, "14e4-1648", "14e4-1648", 0),
PCI_ROM(0x14e4, 0x164d, "14e4-164d", "14e4-164d", 0),
PCI_ROM(0x14e4, 0x1653, "14e4-1653", "14e4-1653", 0),
PCI_ROM(0x14e4, 0x1654, "14e4-1654", "14e4-1654", 0),
PCI_ROM(0x14e4, 0x165d, "14e4-165d", "14e4-165d", 0),

Recompiled the kernel and a rEFIt -> iPXE boot actually got the Link up on the network card and I can see the requests in the DHCP server logs. However, the iPXE command: ifstat shows 0 RX and 0 RXE. As if the response packets are not being captured. At this point I am dead in the water.


So, 

My question is. How do I get these Mac Minis to perform a PXE boot of the Ubuntu LTSP 12.04.4 thin client? Any help would be appreciated.

---

### Post by charlieott on 2014-04-23
So I noticed that it is possible to boot Ubuntu EFI on the Mac Mini.  So perhaps it is possible to boot a LTSP Thin Client from a Boot Disc or USB drive?

---

### Post by coolguy-net on 2014-05-17
Were you able to figure this out? 

I want to use a Mac Mini as an LTSP server. Is it possible? Drivers and compatibility is my main concern. Thunderbolt to Ethernet adapter can be second NIC. Thoughts?

---

### Post by bapoumba on 2014-05-17
*Thread moved to **Apple Users**.*

---

