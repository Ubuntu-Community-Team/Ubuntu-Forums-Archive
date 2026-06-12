---
title: "Adding extra drive(s)"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by FriscoZR on 2007-04-24
Is there a how to on adding extra drives?
Maybe my brain is just fried but I don't seem to be able to find one to ck what I've done.

Did a fdisk and mkfs to full disk.
Can see volume(s) in file browser. When dbl click, it changes reference in left panel to disk or disk-1 in case of two/second drives (actually adding 2 of them).

Why doesn't this happen automatically? Did I miss something? I'm sure a DOH is coming....
This causes other issues down the line - somba cfg.

Hopefully someone can point me in the right direction or tell me what's going on.

Thanks a bunch in advance
MP

---

### Post by kidders on 2007-04-26
Hi there,

What would you like to have happen automatically?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by FriscoZR on 2007-04-26
For the drives to be consistantly seen as the 'disk' or 'disk-1' or some other label that I can reference.
Under Windows after going through the process. The drive shows up as a letter or multiple letters if it was partitioned that way. Now the little info I saw said to use either mkfs or gparted not sure if I should have used both. I just used mkfs since that's what they did.

I'm sure it's possible, actually I'm quite sure, I just don't quite understand the whole process here of how to add and additional drive and then be able to use it under Linux/Utunbu.

Any additional light that you or anyone else is willing to shed, is quite welcome.

Thanks,
MP

---

### Post by kidders on 2007-04-26
Hey again,

The process is the same as on any other OS, really. To use a hard disk, you need to create a partition table, and one or more filesystems. On Linux, once you've done that much, you can add lines to /etc/fstab to control how/where your new filesystems show up.

> For the drives to be consistantly seen as the 'disk' or 'disk-1' or some other label that I can reference.Generic labels like these will probably get used if you forget to label your filesystems. Mounting things in /media often makes them show up as separate devices in filesystem browsers. (I'm guessing that what you're referring to ... or do you mean /dev labels?)

Personally, I tend to use cfdisk and mkfs to set up new disks. Gparted, etc. do more or less the same thing, but if you do it yourself, you get better control over command parameters, which can be nice.

---

### Post by FriscoZR on 2007-04-26
Yes - I think that's exactly what's happening - they are showing up under /media/disk(-1) but only after I try to access them from file browser.

Will you please provide an example of how the cmd line arg's should be to do this properly and what type of entry should be made to that file for the filesystem to be recognized.

It sounds like I need to redo the process.

Thanks again for the asist.
MP

---

### Post by kidders on 2007-04-26
> **FriscoZR said:**
> Yes - I think that's exactly what's happening - they are showing up under /media/disk(-1) but only after I try to access them from file browser.That's probably what's *supposed* to happen, in that a device need only be mounted when you want to use it (unless of course your /etc/fstab says otherwise).

Could you post your current /etc/fstab, and perhaps the output of a **sudo fdisk -l**.

---

### Post by FriscoZR on 2007-04-26
I'll get that for you as soon as I can. But I'm not at a place I can do that right now. Maybe later this afternoon or tonight.

---

### Post by FriscoZR on 2007-04-28
Here's the response to the cmd line

Disk /dev/hda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4754    38186473+  83  Linux
/dev/hda2            4755        4963     1678792+   5  Extended
/dev/hda5            4755        4963     1678761   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

### Post by FriscoZR on 2007-04-28
here's the fstab file contents

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1ef3575a-1b50-49c2-997f-362b42b6badf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=40afc97c-8355-4813-b453-7e2bd592e1bb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by kidders on 2007-04-28
Hmm... so I'm guessing you've added two new SCSI devices?

How about adding something to your /etc/fstab along the lines of "**/dev/sda1 /media/whatever whateverfs defaults 0 0**" ? Exactly what to add depends on what kinds of filesystems you've created, and where you want to mount them.

---

### Post by FriscoZR on 2007-05-13
Sorry, I've been travelling for 2 weeks. So, I've not been able to do anything with this.
Where do I find about the options at the end of the line? I generally understand what you're saying but I would like to be more knowledgeable about what I'm doing or have done.

I've not added scsi devices but sata devices and I guess that those are considered under the scsi interfaces as far as linux is concerned.

Thanks again for the assist.
MP

---

### Post by kidders on 2007-05-13
No problem. :-)

The man pages for **fstab** and **mount** are the best places to look for more information.

The one important thing to remember about /etc/fstab is not to reboot your machine unless you're sure about the correctness of what's in it. If you accidentally ask your system to do something crazy, it might not boot!

**Edit:** Sorry... you're right about SATA devices... they normally use a serial interface in Linux.

---

### Post by FriscoZR on 2007-05-14
Thanks for the sage advice. I doubt I'll have too much to worry about with boot since these are aux drives. But I'm tallented, so anything is possible.
Where are the main (man? sic/typo?) pages? (My nube is showing) Assuming some sort of ref to help docs or pages? Or are they man/manual pages? I'll go hunt around a bit...

Thx again,
MP

---

### Post by kidders on 2007-05-14
Virtually every single package on your machine has a man(ual) page (or a whole set of them). I was suggesting typing **man mount** or **man fstab** for some detail. Be warned though ... **mount**'s man page is ... how should I describe it ... ehh ... comprehensive.

---

