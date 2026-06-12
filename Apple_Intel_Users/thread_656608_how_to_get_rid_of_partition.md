---
title: "how to get rid of partition"
date: 2008-01-02
forum: Apple Intel Users
---

### Post by stealthsniper96 on 2008-01-02
i need to know how to get rid of my ubuntu partition so that i can install it through vmware instead. i installed it by creating the origional partition using BC, then deleting it in Ubuntu and installing on the free space. thanks.

---

### Post by alephsmith on 2008-01-03
If you use leopard you should be able to remove you linux partitions using Disk Utility. Select your internal disk and go to the partition tab to remove the extra partition.

If you use Tiger you may need to use the OS X installation dvd as described here: [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#Restoring_your_Mac_to_its_original_state](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#Restoring_your_Mac_to_its_original_state).
Basically you remove your linux partitions to fool bootcamp into thinking you have an unmodified HDD. Then you use bootcamp create a new 'Windows partition' and then restore your drive back to its original state.

---

### Post by ronocdh on 2008-01-03
I always use the [GParted]("http://gparted.sf.net") CD when messing around with partitions. Removing them outright is of course an option, but it also supports resizing of filesystems like ext3 and fat32 (not hfs+, sadly).

I have only needed to resort to the OS X DVDs when I want to change the size of my OS X partition. You can do this without data loss by using the disc to create an image of your OS X partition (save to an external), then reformatting with new partition sizes and restoring from the image.

---

### Post by cyberdork33 on 2008-01-04
> **ronocdh said:**
> I always use the [GParted]("http://gparted.sf.net") CD when messing around with partitions. Removing them outright is of course an option, but it also supports resizing of filesystems like ext3 and fat32 (not hfs+, sadly).

I have only needed to resort to the OS X DVDs when I want to change the size of my OS X partition. You can do this without data loss by using the disc to create an image of your OS X partition (save to an external), then reformatting with new partition sizes and restoring from the image.GParted can shrink HFS+, just not grow it. Also, Parted Magic can create a totally new HFS+ partition.

I still think it is easiest with the latest version of Disk Utility... just select the partition you want to get rid of, and click the minus button, and the other partitions take up the space.

---

### Post by stealthsniper96 on 2008-01-04
ok i tried that way but its not working to well. acording to DU my OS X partition is about 132 gigs, and the linux swap is 737 megs, andthen theres around 12 gigs of just random space thats sorta connected to my mac partition but it gives me an error when i try to tell the journaled partition to use it. whats goin on? when i try to delete the linux swap, it says it deleted it but it doesnt go away? suggestions?

[IMG]http://i182.photobucket.com/albums/x269/stealthsniper96/Picture5-1.png[/IMG]

[IMG]http://i182.photobucket.com/albums/x269/stealthsniper96/Picture4-2.png[/IMG]

---

