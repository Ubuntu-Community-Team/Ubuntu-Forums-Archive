---
title: "Mounting a USB Drive"
date: 2009-04-27
forum: Apple Hardware Users
---

### Post by gsp8181 on 2009-04-27
Hello

I have a LaCie Big Disk Extreme+ (1tb) formatted for use with OS X Intel (Uses the Apple Partition Map Partition Table with a single HFS+ partition)
I am trying to get it to mount in Ubuntu, I know HFS+ Works as I can mount my HFS+ APM iPod, but strangely not my LaCie

Mounting results in errors but in messages I get some information

```
Apr 27 18:36:32 ... kernel: [ 4481.336032] usb 1-7: new high speed USB device using ehci_hcd and address 22
Apr 27 18:36:32 ... kernel: [ 4481.472482] usb 1-7: configuration #1 chosen from 1 choice
Apr 27 18:36:32 ... kernel: [ 4481.498538] scsi8 : SCSI emulation for USB Mass Storage devices
Apr 27 18:36:32 ... kernel: [ 4481.511413] input: LaCie    LaCie Big Disk Extreme+ as /devices/pci0000:00/0000:00:03.3/usb1/1-7/1-7:1.1/input/input15
Apr 27 18:36:32 ... kernel: [ 4481.521876] generic-usb 0003:059F:0829.000D: input,hidraw4: USB HID v1.11 Device [LaCie    LaCie Big Disk Extreme+] on usb-0000:00:03.3-7/input1
Apr 27 18:36:37 ... kernel: [ 4486.501761] scsi 8:0:0:0: Direct-Access     LaCie    BigDisk Extreme+ GM4O PQ: 0 ANSI: 4
Apr 27 18:36:37 ... kernel: [ 4486.505069] sd 8:0:0:0: [sdd] 1953546240 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr 27 18:36:37 ... kernel: [ 4486.505621] sd 8:0:0:0: [sdd] Write Protect is off
Apr 27 18:36:37 ... kernel: [ 4486.510015] sd 8:0:0:0: [sdd] 1953546240 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr 27 18:36:37 ... kernel: [ 4486.516229] sd 8:0:0:0: [sdd] Write Protect is off
Apr 27 18:36:37 ... kernel: [ 4486.516256]  sdd: unknown partition table
Apr 27 18:36:37 ... kernel: [ 4486.543590] sd 8:0:0:0: [sdd] Attached SCSI disk
Apr 27 18:36:37 ... kernel: [ 4486.543766] sd 8:0:0:0: Attached scsi generic sg4 type 0
```

Any help is appreciated :)

---

### Post by gsp8181 on 2009-04-27
fdisk gave me
```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x347ee774.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 121602.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): P

Disk /dev/sdd: 1000.2 GB, 1000215674880 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x347ee774

   Device Boot      Start         End      Blocks   Id  System

Command (m for help):  
```

---

### Post by cyberdork33 on 2009-04-27
this is just a guess, but it sounds like your kernel is compiled without support for the Apple Partition Map support.

Try a GUID partition table (GPT) or MDOS format. on your disk (which OSX will also support).

---

### Post by gsp8181 on 2009-04-28
> **cyberdork33 said:**
> this is just a guess, but it sounds like your kernel is compiled without support for the Apple Partition Map support.

Try a GUID partition table (GPT) or MDOS format. on your disk (which OSX will also support).

That would mean Reformatting the disc, As it contains 800GB of data, thats not easy to backup and format :)

Know how/where I could go to learn how to add APM support to the kernel? (Well, where I could get the patch for APM?)

Thanks

---

### Post by cyberdork33 on 2009-04-28
> **gsp8181 said:**
> That would mean Reformatting the disc, As it contains 800GB of data, thats not easy to backup and format :)

Know how/where I could go to learn how to add APM support to the kernel? (Well, where I could get the patch for APM?)

Thanks
so copy it off, reformat, and copy it back...

it is just an option in the kernel config. you can google info about compiling your own kernel. No patch is needed.

---

