---
title: "Partition and Swap blues"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by saxuntu on 2007-08-27
Trying to set up my wife's laptop for an XP/dapper dual boot. I setup an ext3 partition using Knoppix QTparted (Gparted was being fussy). Now its not letting me create a swap partition, saying i can only have 4 primaries and i need to create an extended (which neither program will give me an obvious answer to do). After searching the forums the swap file looks like less of a headache to create (thanks to the community FAQ). However there appears to be some debate over the wisdom of this solution. So the question:

Figure out how to create a 256mb extended partition or Swap file? (the latop already has 1gb ram).

---

### Post by LaRoza on 2007-08-27
> **saxuntu said:**
> Trying to set up my wife's laptop for an XP/dapper dual boot. I setup an ext3 partition using Knoppix QTparted (Gparted was being fussy). Now its not letting me create a swap partition, saying i can only have 4 primaries and i need to create an extended (which neither program will give me an obvious answer to do). After searching the forums the swap file looks like less of a headache to create (thanks to the community FAQ). However there appears to be some debate over the wisdom of this solution. So the question:

Figure out how to create a 256mb extended partition or Swap file? (the latop already has 1gb ram).

I use GParted on Live CD, in my sig, in that, you can easily create a new partition as an extended partition.

To clarify:
* A harddisk can have 4 primary partitions
* An extended partition IS a primary partition
* An extended partition need to have "logical drives", to be used.
* A logical drive behaves as a partition, in Windows, they get there own drive letters, in Linux, you can mount them just like a primary partition.

You have, from what I see, an NTFS partition already, with Windows. You will need a EXT3 partition for Ubuntu + a Swap partition. You should also add a data partition for sharing data, but that is not needed.

So:

0. Shrink the NTFS partition to the smallest size you can afford (leave room for installing programms, if you intend to)
1. Create three primary partitions: one EXT3 ~10 gig, one Linux-Swap 256 MB (as you said), and a third with FAT32 as the rest of the harddisk (for data). 
2. Install / of Ubuntu to the ext3 partition and use swap.

For the fourth partition recommendation, use a different file system if you want to save files larger than 4 GB. 

If you have a "recovery partition", which may be hidden, you can delete that, if you want. If the Windows installation gives you an option to make "recovery disks", do so, if you feel you want the ability to restore the laptop to OEM condition.

---

### Post by saxuntu on 2007-08-27
I'm going to sort of follow your advice. I'm making recovery dvds and will wipe out the recovery section. There's a mystery 1gb partition, i'm wondering if it runs HP's Quickplay garbage. I'm leaving the majority of the HD ntfs for XP because its my wife's computer and i'm putting Ubuntu on for me. I'm going to make the 10gb recovery the ext3/Linux and then make the swap. That should be 4 and everyone's happy.

Thanks for the advice, should have thought of it myself. Also thanks for the HD partition info. Good to know.

---

### Post by Inxsible on 2007-08-27
> **saxuntu said:**
> I'm going to sort of follow your advice. I'm making recovery dvds and will wipe out the recovery section. There's a mystery 1gb partition, i'm wondering if it runs HP's Quickplay garbage. I'm leaving the majority of the HD ntfs for XP because its my wife's computer and i'm putting Ubuntu on for me. I'm going to make the [COLOR=Red]10gb recovery[/COLOR] the ext3/Linux and then make the swap. That should be 4 and everyone's happy.

Thanks for the advice, should have thought of it myself. Also thanks for the HD partition info. Good to know.

HP had a 10GB Recovery partition !!!!!!!

When I bought mine, it had a 6.85GB HP Recovery partition. I just nuked the damn partition. Damn waste of space I should say. Because when the Windows goes bad, I ain't recovering it !!!!

:)

---

### Post by saxuntu on 2007-08-28
Hahaha touche sir

I blew away the recovery partition after making backup discs. Its the wife's computer, she wants windows, i try to get her to use linux but no go. I guess this is one of the "worse" things. Anyway Ubuntu is on the thing and was easier to install on it than my desktop. Love this OS.

---

