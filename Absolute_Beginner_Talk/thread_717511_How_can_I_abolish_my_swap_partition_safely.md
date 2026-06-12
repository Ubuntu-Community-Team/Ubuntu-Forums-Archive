---
title: "How can I abolish my swap partition safely?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Vode on 2008-03-07
Okay. At the moment my hard drive is partitioned as so:

[IMG]http://i92.photobucket.com/albums/l24/VodeAndreas/Screenshot--dev-sda-GParted.png[/IMG]

I want to completely remove my swap partition and merge the former swap and the other couple of megs of unallocated space into my Ubuntu partition at the end of the drive.
I have the latest Gparted live CD on hand and ready to remove it, but will merging the partition in before the start of my current Ubuntu partition affect regular operation (not in relation to the removal of a swap, I know how swap works)?

An additional piece of information that I think I'll need to change for this to work, being fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4058189c-c8a5-4ce0-b504-a2f834e108d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
# /dev/sda2
UUID=b0a725cf-5ab9-49c5-8f10-a14ae4325097 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
```

I went through the first two pages of results for a search of swapoff and looked at the possibly related threads when I wrote in my title but the only threads I noticed were in relation to enhancing/creating/juggling swap not removing it altogether.

Thanks, Vode.

---

### Post by dptxp on 2008-03-07
i do not think that you can merge your sda2 with sda3 without deleting sda3 (and its data). You can merge it with the unallocated space.

---

### Post by celticbhoy on 2008-03-07
To be honest I would think that looking at the abount of data on each drive, the best bet would be to back up your linux data to the windows drive and re-install. I think if you were just to merge the space and swap partition you would be opening a can of worms, as it is at the start of the partition.

---

### Post by Paqman on 2008-03-07
> **dptxp said:**
> i do not think that you can merge your sda2 with sda3 without deleting sda3 (and its data). You can merge it with the unallocated space.

No, you can do that. When you delete sda2 it will just become unallocated space. Then you can expand sda3 to use that space. That operation might take quite a while. Back sda3 up before touching it.

You probably *could* possibly run quite happily without a swap, but it depends on your hardware. Since you've got tons of free space in your Linux partition I don't see any advantage in getting rid of it, though. Why did you want to get rid of it?

---

### Post by Vode on 2008-03-07
The highest RAM usage I've ever seen on here is ~40% (768 total) and highest swap usage ~30MB, it doesn't really need to be there.

I think from what people here have said I might wait until next month and do a full backup and reinstall of my linux partition with Hardy. More replies on how possible this is are welcome however.

I can open:
Firefox, GIMP, Adobe Acrobat 8, Open Office Writer, Pidgin, kTorrent, etc. (more than I'd ever be using at once on here) and still only be using 47% RAM at peak (with ~16 tabs open, largest image I have, etc.)

---

