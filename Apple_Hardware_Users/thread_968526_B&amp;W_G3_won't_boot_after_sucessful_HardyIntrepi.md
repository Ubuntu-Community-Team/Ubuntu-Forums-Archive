---
title: "B&amp;W G3 won't boot after sucessful Hardy/Intrepid install"
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by hopefulone on 2008-11-02
Okay, I have been searching for days to find a solution to this. I am able to run Hardy Live CD fine and it installs without error. I even tried alternate install CDs -successful install for both Hardy and Intrepid. After install the system gets through most of the boot process but it stalls when scanning the disks (and partitions?)at:
 
 scsi0 : MESH
 hde: max request size: 128KiB

with lost interrupt messages and DMA interrupt recovery nonstop. I watch the output up to the hang through the nosplash option in yaboot.conf.

The boot process stops at the same stage in both Hardy and Intrepid. 

I have already tried noapic, nolapic, ide=nodma, etc. to no avail. Any ideas? 

I have an ACARD 6260 PCI/IDE card with all drives attached as this is a rev.1 B&W. 

Help!

---

### Post by DRM_free on 2008-11-03
Open a bug report on [http://bugzilla.kernel.org](http://bugzilla.kernel.org) and email the details of your problem to [email]linux-ide@vger.kernel.org[/email] .

---

### Post by hopefulone on 2008-11-03
Bug opened. Thanks for the guidance. 

[http://bugzilla.kernel.org/show_bug.cgi?id=11943](http://bugzilla.kernel.org/show_bug.cgi?id=11943)

---

### Post by stream303 on 2008-11-03
Is your hard drive larger than 128gb?

Part of the problem may be that G3 B&W Powermacs have a 128gb partitioning limitation in firmware that the root partition cannot exceed, and the Ubuntu installer does not know about.  This can be overcome with manual partitioning - I cheat by using the "go back" feature of the partitioner to just delete the pre-existing swap, then resize the root partition to UNDER 128 gb, like 125 or so, make the rest of the disk an ext3 /home, and make a 2x swap.

There may also be UUID issues in /etc/fstab, but it's been awhile since I helped install a B&W.

---

### Post by hopefulone on 2008-11-03
No, all under 128 GB. Ubuntu is on a 100 GB drive (hde), OS X data drive of 120 GB (hdf) and OS X itself on another 100 GB drive (hdg). 

I thought about moving the Ubuntu drive to the onboard controller but I remember having two drives corrupted there years ago which is why the 6260 is in use. Boots great in OS X (yaboot included) and most of the way in Hardy and Intrepid...

When I have looked in fstab it only shows the root and swap partitions on hde. Nothing from the other drives is listed but I didn't expect them to be  listed since they are OS X disks. 

I admit being a Linux noob so am not quite sure what to expect when viewing files yet.  :)  I appreciate your response.

Another question, the Kernel Bug Tracker has asked me:
"Could you try some newer kernel like 2.6.27 or 2.6.28-rc3?

Can I do that when I can only run from the Hardy Live CD or alternate CD's?
If so, how?

Thanks.

---

### Post by hopefulone on 2008-11-04
Another question, the Kernel Bug Tracker has asked me:
"Could you try some newer kernel like 2.6.27 or 2.6.28-rc3?

Can I do that when I can only run from the Hardy Live CD or alternate CD's?
If so, how?

Thanks.

---

