---
title: "How to repair and install a damaged hard disk"
date: 2014-01-01
forum: Any Other OS
---

### Post by Jonatan Formentera on 2014-01-01
Hi,
I have a netbook:
Intel N570
Intel Graphics Media Accelerator 3150
! GB DDR3 Memory 250 GB HDD 
802.11b/g/n 10.1 LEDLCD (1024x600)
I made a mistake by trying to create a partition in the harddisk and damaged it. Now I can just start the computer but can neither access to the contest nor reconfigurate it by using the BIOS. I have taken the computer apart and taken out the hard disk. I have formatized it using an USB enclosure with another computer. I'd like to know if I could install a Linus OS in it by using an enclosure and another computer. Perhaps so I could make my netbook work
Thanks

---

### Post by tgalati4 on 2014-01-01
Yes, your processor can use 64-bit, so install that:  [http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz](http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz)

Pop it in and it should work.  There may be a few things that need fixing.  Just post them in this thread as they come up.  Try working on one problem at a time.

---

### Post by Jonatan Formentera on 2014-01-01
OK I've downloaded the OS win7.exe. What's the next step? Do I have to copy it in the hard disk and simply double click or do I need more steps?
Thanks

---

### Post by bapoumba on 2014-01-01
Moved to Other OS/Distro Support.

---

### Post by philinux on 2014-01-01
> **Jonatan Formentera said:**
> Hi,
I have a netbook:
Intel N570
Intel Graphics Media Accelerator 3150
! GB DDR3 Memory 250 GB HDD 
802.11b/g/n 10.1 LEDLCD (1024x600)
I made a mistake by trying to create a partition in the harddisk and damaged it. Now I can just start the computer but can neither access to the contest nor reconfigurate it by using the BIOS. I have taken the computer apart and taken out the hard disk. I have formatized it using an USB enclosure with another computer. I'd like to know if I could install a Linus OS in it by using an enclosure and another computer. Perhaps so I could make my netbook work
Thanks

Are you trying to install ubuntu or rescue windows?

---

### Post by Jonatan Formentera on 2014-01-01
Anyone. I just want to install an OS and after that I will install Ubuntu

---

### Post by sammiev on 2014-01-01
You should be able to download the Windows ISO from their site and install it to a USB and boot from that to install to your HD. At some point in the install it will ask you for your key. If you made a copy of your installation windows to DVD/USB then your good to go as well.

---

### Post by Jonatan Formentera on 2014-01-01
I tried that but it didn't work. The problem is the boot menu in the BIOS is disable and I can't enable it. It can't read the hard disk. Perhaps it is a problem of the BIOS. I don't really know

---

### Post by oldfred on 2014-01-01
You cannot install Windows to an external device. And it has to be installed to the same system as you are using.

Linux can usually install to external devices and boot on any system, as long as proprietary drivers are not required. Sometimes video, Ethernet or specific hardware needs extra drivers to have it fully work on a different system, but often defaults or adding boot parameters will let you boot.

---

### Post by Jonatan Formentera on 2014-01-01
I have installed microde-20130808.tgz in the hard disk and it appears on the screen:
For Atheros PCIE Ethernet Controller v2.0.2.2 (03/31/10)
Check cable connexion!
PXE-MOF: Existing Intel PXE Rom
No bootable device- insert book disk and press anykey
Intel UNDI, PXE-2.8 (build 083)
I've   made a pen drive bootable, but it doesn't work. I don't know whar can I  do. Perhaps it's a question or drivers or I haven't found the correct  software to boot it

---

