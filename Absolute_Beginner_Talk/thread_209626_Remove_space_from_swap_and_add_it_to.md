---
title: "Remove space from swap and add it to /"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by b4lr0g on 2006-07-05
Hi,

    I'm running Dapper on a HP dv4000 laptop with 1 Gig RAM. I dual boot with Win XP.  I've got 1 Gig of RAM and created a 2 Gig swap partition during installation. Creating a swap partition with twice the amount of RAM seemed like a good idea, considering my old desktop had just 256 MB of RAM and it needed 512M swap. But now, I realized I don't need that kind of swap at all with 1 Gig of RAM. I'd be having terrible time working if I actually /needed/ that much of swap anyway :) 

   All I want to do now is to bring the swap space down to 512M and add the rest of 1.5 Gig to / partition. Is there any way to do that? 

   After a bit of Googling around, I came across the links to add / delete swap space but not remove some space from swap and add it to an existing partition :( 

   Any pointer to a HOWTO will be real helpful. 

   Here are my disk partiotions, if necessary

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         920     7389868+   7  HPFS/NTFS
/dev/hda2             921        9703    70549447+   f  W95 Ext'd (LBA)
/dev/hda3            9704        9729      208845   88  Linux plaintext
/dev/hda5             921        2883    15767766    7  HPFS/NTFS
/dev/hda6            2884        8655    46363558+   7  HPFS/NTFS
/dev/hda7            8656        9442     6321546   83  Linux
/dev/hda8            9443        9703     2096451   82  Linux swap / Solaris

   Thanking you in advance.

---

### Post by bruenig on 2006-07-05
Tthe way I would try to do this is put in the ubuntu live cd, go to system>administration>gnome partition editor, and then resize the swap and resize the / to absorb the new space. Doing this will get by the fact that you wont have to mess with mounted partitions as it would if you did this when booted. Apply changes shutdown take the cd out and reboot.

May not work as resizing the swap may require a reformat.

---

### Post by cowley on 2006-07-05
i use gparted livecd for adjusting partitions after ubuntu installs

simon

---

### Post by confused57 on 2006-07-05
I have the same dilemma, 1Gb ram & 2 Gb swap and need to reduce the size of swap also.   I'm thinking I'll need to delete the swap partition, resize the partition before it to all except 512 Mb, then create a new partition for swap on the remaining 512 Mb.
I'll be interested in the replies that you get, cause I'm not sure if the way I've described is the best way to go about it.

After reading your other replies,  gparted live cd would be able to resize swap, but I was concerned that it would leave unallocated space after the resized swap partition...swap may be different when resizing, I don't know.

---

### Post by cowley on 2006-07-05
use gparted livecd - it will allow you to resize the swap and then take the then unallocated disk space elsewhere.  

simon

---

### Post by b4lr0g on 2006-07-05
[QUOTE=cowley]use gparted livecd - it will allow you to resize the swap and then take the then unallocated disk space elsewhere.  

simon[/QUOTE]

Thanks a lot. I'll try it as soon as i get home.

---

### Post by b4lr0g on 2006-07-06
Worked like a charm. :) 

The interface is so similar to PartitionMagic and due to my familiarity with it, I found it very easy to do it. 

I can't thank you guys enough. 

:-D

---

