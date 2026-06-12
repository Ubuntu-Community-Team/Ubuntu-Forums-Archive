---
title: "Un-doing a partition"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by dvryan on 2007-10-09
I've been having problems trying to re-size my 2 partitions.  Since I just installed Ubuntu and have nothing customized on it, I'm thinking of deleting the ubuntu partition, enlarging the windows partition to encompass the entire hard drive, then re-partitioning and re-installing ubuntu on a re-sized partition.

My questions- can this work?  If I use the ubuntu cd to delete the ubuntu partition, will that same cd let me re-size my windows partition to encompass the whole drive?  To date, it won't let me increase the windows partition for some reason.  When I erase the ubuntu partition, will I have to re-format the unallocated space to NTFS?  Will that allow me to make the windows partition bigger?

---

### Post by FuturePilot on 2007-10-09
Yes it will let you do that. You could also just delete the Ubuntu and swap partitions and then run the installer and there will be an option to Use Largest Continuous Free Space. That will then install it back where it was just removed from.

---

### Post by strabes on 2007-10-09
> **dvryan said:**
> If I use the ubuntu cd to delete the ubuntu partition, will that same cd let me re-size my windows partition to encompass the whole drive?  To date, it won't let me increase the windows partition for some reason.

The gutsy live CD should. If not, you can use a [gparted live CD](http://gparted.sourceforge.net/livecd.php) to do that.

>  When I erase the ubuntu partition, will I have to re-format the unallocated space to NTFS?  Will that allow me to make the windows partition bigger?

No, you won't **have** to do anything. You can simply leave the empty space created by deleting your ubuntu partition unallocated.

I advise you to not make too many unnecessary size changes to your partitions, especially to those that are NTFS.

---

### Post by goodboyCerberus on 2007-10-09
Here's a partitioning guide:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

"The focus of this tutorial is not on *how* to create the partitions (resizing, etc.) but on planning&#8212;what the desirable outcome is."


If you encounter problems try searching the GParted support forum:
[http://gparted-forum.surf4.info/viewforum.php?id=2](http://gparted-forum.surf4.info/viewforum.php?id=2)

Good luck!


Oh, and here's a preview of what GParted looks like:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by dvryan on 2007-10-09
>Yes it will let you do that. You could also just delete the Ubuntu and swap partitions and then run the i>nstaller and there will be an option to Use Largest Continuous Free Space. That will then install it back >where it was just removed from.

What do you mean by swapping partitions?  I just want to delete linux and that partition, make the windows partition bigger, then add linux back on to the now-smaller partition.  Do I have to swap partitions for that?

---

### Post by FuturePilot on 2007-10-09
Linux uses a small partition for swapping stuff out of RAM to the hard drive. Similar to the page file in Windows. If you don't delete that partition along with the Ubuntu partition you will end up with 2 swap partitions when you reinstall.

---

### Post by Paqman on 2007-10-09
A "swap" partition is a small partition that Linux systems generally have. If you look at your drive in Gparted you'll probably see a very small partition with the filesystem "Linux swap".

---

### Post by dvryan on 2007-10-09
Gotcha- thank you.

- Dan

---

### Post by dvryan on 2007-10-09
I have a big problem!  This is what happened:

1) I erased the Ubuntu partition.  I could not erase the swap partition- it was mounted, and I couldn't figure out how to unmount it.

2) when I rebooted my PC, I get this:

"GRUB loading stage1.5

GRUB loading, please wait . . .
Error 22"

And it stops.  Please help!  How do I fix this?

---

### Post by FuturePilot on 2007-10-09
To unmount the swap right click on the entry in GParted and select Swap Off. Then you can delete it. You should then install immediately after that. You won't be able to boot the computer because Grub will be looking for something that isn't there.

---

### Post by dvryan on 2007-10-09
Will I get that error screen even after deleting the swap partition?  Do I have to format everything and start over?

---

### Post by FuturePilot on 2007-10-09
> **dvryan said:**
> Will I get that error screen even after deleting the swap partition?  Do I have to format everything and start over?

Yes. If you delete the swap partition you will still get that error if you try to boot off the hard drive. You need to reinstall Ubuntu again before you try booting off the hard drive.

---

### Post by dvryan on 2007-10-09
I turned swap off but it still won't let me delete it- I can reformat it to ntfs or something else, but can't delete it.  Any ideas?

---

### Post by dvryan on 2007-10-09
I massaged it a bit and managed to get the swap partition deleted- back to just one partition.  Now, I want to make two partitions, and put Ubuntu on one, and XP on the other.  I guess I have to do the Ubuntu one first?  Will XP have trouble with that?

---

### Post by FuturePilot on 2007-10-09
Do you already have XP on the other partition already?

---

### Post by dvryan on 2007-10-09
Yes, but when I deleted my ubuntu partitions, that's when I started having problems booting the machine.  So, now (according to gparted) I have 1 partition of 110GB, and it says 107GB are full.  My XP partition, before all this, was 20GB, and 17GB full.  When I deleted the original Ubuntu partition, and expanded the XP partition to include the space left available from deleting, that's when the hard drive usage went up and my machine stopped booting properly.  Does that make sense?  

So, the way I see it, I need to re-partition the hard drive into two parts, and put Ubuntu on one, and XP on the other.  I"m just wondering how to put XP on one first, since I'm having problems booting and can't do much.

---

### Post by FuturePilot on 2007-10-09
The reason you can't boot the computer is because Grub is looking for Ubuntu but it's not there. You could have left the XP partition alone and just had the install use the free space. But now that you've got it expanded on the entire hard drive just start the installer and tell it to resize the partition. It should be the default choice. You won't have to reinstall XP.

---

### Post by dvryan on 2007-10-09
That makes sense.  I'm still running into a problem, though- it won't let me partition my drive because my drive (it thinks) is almost full- 117GB full out of 120.  When I try to partition it (100GB and 20GB) it gives me errors and won't let me.  Any way I can delete only part of the partition?  It won't let me resize it.

---

