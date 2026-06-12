---
title: "No option for resize install"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by dgbearcat on 2008-01-31
[B]Ok, so I've decided to install Ubuntu after using it on a liveCD for a while. 

Problem is, I want to have Ubuntu partition things out automatically as seen here:[/B]

**However, my only options are shown here:**



**I'm missing the "step 4" shown here as well:**


[B]
I usually use XP, but there are some linux apps I'd like to use, and I'm considering possibly switching to it as my main OS. I've got an 80 gig HD, with about 25-30 gigs of that free. I know Ubuntu needs about 8 gigs, and I'll probably install a few programs into it but not much. 

If no one knows why I'm missing that option, I could potentially do the manual partition. When I select that option, here's what I get:[/B]


[B]
Thanks in advance for any help you can provide.[/B]


Edit bodhi.zazen: Oh my, those screen shots are much too bog. Please use thumbnails

[noparse][[img]http://url_thumbnail[/img]](http://url_big_picture)[noparse]

---

### Post by The Cog on 2008-01-31
You don't have any free space which is why you don't see the option to use free space. 
sda1, 49M will be a recovery or a utility partition. Leave it alone.
sda2, 96G is your C: drive
sda3, 3.8G is probably showing in Windows as D:
And that's the whole disk used up. No free space.

3.8G is just enough space for Ubuntu if you want ot delete that partition. The easieat way would be to delete the third partition (use windows to do it if you're more comfortable that way) then restart the installer and choose to use the free space.

You could also choose to reduce the size of the NTFS partition to make some space if you prefer.

---

### Post by dgbearcat on 2008-01-31
> **The Cog said:**
> You don't have any free space which is why you don't see the option to use free space. 
sda1, 49M will be a recovery or a utility partition. Leave it alone.
sda2, 96G is your C: drive
sda3, 3.8G is probably showing in Windows as D:
And that's the whole disk used up. No free space.

3.8G is just enough space for Ubuntu if you want ot delete that partition. The easieat way would be to delete the third partition (use windows to do it if you're more comfortable that way) then restart the installer and choose to use the free space.

You could also choose to reduce the size of the NTFS partition to make some space if you prefer.


The drive is 89.5 GB capacity, and windows tells me there's about 30 gigs left on it. I have no idea what it thinks D is unless it's my CD drive. I definitely have free space on C.

Do I have to partition it ahead of time? I guess I thought that Ubuntu would take the spare NTFS space and turn it into FAT for me and then put Ubuntu there.

---

### Post by The Cog on 2008-02-01
The screen dump above shows 3 partitions. Partition 2 is the big NTFS one, and that is definitely going to be your Windows partition. I can only guess at what 1 and 3 are - or rather, I can't guess. It would be interesting to know what the XP disk tool says about your partitions - right-click My Computer and choose Manage, then Storage->Disk Management. Anyway, I would be inclined to leave 1 alone - it may well be a recovery partition or a set of DOS based diagnostics that the BIOS can boot into.

Space which is "free" on your Windows partition cannot be directly used by another partition. Like your neighbours free floor space can't be part of your house without moving some walls first. Free space inside a partition doesn't help in this case, other than meaning you can move the partition boundaries further. To make room for Ubuntu, you need to make some really free space - space that isn't inside any partition. You can gain some by deleting partition 3 if you're sure it doesn't contain anything valuable. You can use the installer to reduce the size of the NTFS partition. Doing both would leave the biggest gap to put Ubuntus partitions into. Vista is able to resize its own partiton even while running on it. That's a neat trick I've not heard of before.

IF XP doesn't have the tools to resize the partition, I think it is actually easier to run gparted from the live CD and make the unpartitioned space before then running the installer and simply choosing to use the free space.

But if you're not sure about doing the partitioning, it may be better to just install another hard disk for Ubuntu and leave your precious Windows disk intact. We don't really want you making a mistake while partitioning then going round telling everyone that Linux trashed your PC - it happens occasionally.

---

### Post by dgbearcat on 2008-02-01
> **The Cog said:**
> The screen dump above shows 3 partitions. Partition 2 is the big NTFS one, and that is definitely going to be your Windows partition. I can only guess at what 1 and 3 are - or rather, I can't guess. It would be interesting to know what the XP disk tool says about your partitions - right-click My Computer and choose Manage, then Storage->Disk Management. Anyway, I would be inclined to leave 1 alone - it may well be a recovery partition or a set of DOS based diagnostics that the BIOS can boot into.

Space which is "free" on your Windows partition cannot be directly used by another partition. Like your neighbours free floor space can't be part of your house without moving some walls first. Free space inside a partition doesn't help in this case, other than meaning you can move the partition boundaries further. To make room for Ubuntu, you need to make some really free space - space that isn't inside any partition. You can gain some by deleting partition 3 if you're sure it doesn't contain anything valuable. You can use the installer to reduce the size of the NTFS partition. Doing both would leave the biggest gap to put Ubuntus partitions into. Vista is able to resize its own partiton even while running on it. That's a neat trick I've not heard of before.

IF XP doesn't have the tools to resize the partition, I think it is actually easier to run gparted from the live CD and make the unpartitioned space before then running the installer and simply choosing to use the free space.

But if you're not sure about doing the partitioning, it may be better to just install another hard disk for Ubuntu and leave your precious Windows disk intact. We don't really want you making a mistake while partitioning then going round telling everyone that Linux trashed your PC - it happens occasionally.

Thanks! I used your and the other advice to use gparted, moved my ntfs down to about 60 gigs and put ubuntu on the rest of it. Works like a charm, although apparently it's somehow messed up standby on windows and standby isn't working at all in ubuntu, but that's a whole different issue.

By the way, it seems that the 1 and 3 partitions were "dell utility" and "dell recovery" partitions, based on the file system setup when I look at it in ubuntu.

---

