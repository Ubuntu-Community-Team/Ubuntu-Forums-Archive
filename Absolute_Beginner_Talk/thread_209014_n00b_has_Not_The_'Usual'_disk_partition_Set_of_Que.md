---
title: "n00b has: Not The 'Usual' disk partition Set of Questions"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by memorex_1 on 2006-07-04
Hi, everyone.  I have Ubuntu 6.06 up and running on a dual boot box with Windows XP.  I am really liking what I see so far in GNU/Linux.  Also, these UbuntuForums.org participants are just awesome folk.

Look just below my questions, you will see a listing of what I see on my hard disk when I use GParted LiveCD.  As you can probably discern by the nature of my questions, I used the Ubuntu Desktop LiveCD installer, and chose the most dumbed-down option for installing Ubuntu onto my existing NTFS hard drive.

But first -- those questions:

(a)  _**Why**_ does the linux-swap file system partition (sda5) get sub-categorized "underneath" an extended partition of the same size (sda3).

(b)  _**What**_ exactly *IS* an extended partition?

(c)  All of my partitions below are reported by GParted as "Not mounted" (or) "Not busy" (or) "Not active".  Is that _**a bad thing?**_

(d)  What _**happened to sda4**_, below?

(e)  When using the _**System-->Disks**_ viewer, sda1 (ntfs) is labeled as "Partition 1".  And sda2 (ext3) is labeled as "Partition 2".  So why is sda3 not labeled at all?

Thanks in advance for your expertise.

Here's that GParted report of my single hard drive:
<w>  /dev/sda1  NTFS  112.25GB  boot  Not mounted 
<x>  /dev/sda2  ext3  115.73GB  Not mounted
<y>  /dev/sda3  extended  4.91GB  Not busy (no mounted logical partitions)
<z>  /dev/sda5  linux-swap  4.91GB  Not active

---

### Post by joft on 2006-07-04
[QUOTE=memorex_1]
(a)  _**Why**_ does the linux-swap file system partition (sda5) get sub-categorized "underneath" an extended partition of the same size (sda3).
[/QUOTE]

I think, that simply this is the way the ubuntu installer does it. There seems to be a rule within it, which says, whenever a swap is created, create it inside an extended partition.

[QUOTE=memorex_1]
(b)  _**What**_ exactly *IS* an extended partition?
[/QUOTE]

An extended partition is a kind of container for N other partitions, called logical partitions. The other partitions are called primary partitions and the point is: usually on x86-architecture you can only create 4 primary or 3 primary+1 extended partitions. That's the way the partition table inside the first sector of your disk is organized.
So, if you want to have more than 4 partitions for data, you have to use an extended and inside that you can create N other partitions.

[QUOTE=memorex_1]
(c)  All of my partitions below are reported by GParted as "Not mounted" (or) "Not busy" (or) "Not active".  Is that _**a bad thing?**_
[/QUOTE]

Can't really help you with that. "Not mounted" means, that a partition is not attached to your file system at the moment and you cannot access the files on the partition. "Not active" might mean, that the "active" byte of this partition's partition table entry is not set. [As long as you have a boot manager like grub which sits on your Master Boot Sector (first sector of disk) it does not hurt having no partition "active".]

[QUOTE=memorex_1]
(d)  What _**happened to sda4**_, below?
[/QUOTE]

sda4 is missing, because you don't have a third primary partition. You have an ntfs primary partition (sda1), an ext3 one (sda2) plus one extend (sda3).
The logical partitions are number from 5, so your first logical partition is of type linux-swap and called sda5.

[QUOTE=memorex_1]
(e)  When using the _**System-->Disks**_ viewer, sda1 (ntfs) is labeled as "Partition 1".  And sda2 (ext3) is labeled as "Partition 2".  So why is sda3 not labeled at all?
[/QUOTE]

sda3 is an extended partition and it simply makes no sense to list that one in the viewer, remember that an extended partition is just a container.

---

### Post by mmmichael on 2006-07-04
I'm kind of a noob myself, but this [http://www.faqs.org/docs/linux_admin/x1139.html](http://www.faqs.org/docs/linux_admin/x1139.html) might help with (a), (b) & (e).

---

### Post by memorex_1 on 2006-07-04
joft --

Thanks so much those excellent answers.  I learned a lot about how hard disks are organized from you!

memorex_1

---

