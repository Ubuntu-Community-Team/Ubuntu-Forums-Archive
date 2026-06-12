---
title: "Installing on any partition?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-07-12
Hi

I was going to install Feisty with XP but can I install on a particular partition of my hard drive. I have already 4 partitions. The largest on (137gb) with XP which I wanted to put Feisty on as well. The others are smaller drives but I wanted to keep them as they are. I use them for backing up data.

When I started installing and it came to the partition part, it showed a message saying 'undetected' or words to that effect in relation to the remaining part of the partition after selecting the first part for XP. (If that makes sense) 

Am I doing something wrong?

Thanks

---

### Post by vineethbs on 2007-07-12
"The largest on(e)  (137gb) with XP which I wanted to put Feisty on as well"

Do you mean to say that you are trying to use the same partition for both WinXP and Ubuntu ? If so, then I don't think its possible.

"When I started installing and it came to the partition part, it showed a message saying 'undetected' or words to that effect in relation to the remaining part of the partition after selecting the first part for XP. (If that makes sense)"

Here, do you mean to say that you selected a part of the 137GB for the WinXP installation ?
Thus, counting the 3 "smaller drives" + this new partition = 4 partitions + free space ?
Are all these "primary" partitions ? If so, then I don't think you can create a partition on the remaining space.

Please clarify my doubts, Thanks :)

---

### Post by louieb on 2007-07-12
Theres some experimental stuff that will allow Linux and XP to live on the same partition.  [Wubi - The Easiest Way to Linux]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html") Haven't tried it myself.

But for the traditional dual boot Linux and windows cannot be installed in the same partition. Since your drive already has 4 partitions. Probably all primary partitions you will need to sacrifice one of them and turn it into an extended partition.  Most Linux installs have 2 partitions one for the OS and one for swap. (virtual memory in windows).   

It can be done, but the way your setup now its not going to be a point and click install. Your going to have to use manual partitioning and set up your partitions in advance of install. You would need to do a major restructure of that hard drives partitions to install Linux.  Check the Dual Boot and psychocats links in signature for more info. 

Sounds to me the easiest way to get Linux on that machine is a second hard drive.  OR try WUBI.

---

### Post by alienexplorers on 2007-07-12
Defrag your windows partition 2 times.  Run the Ubuntu Live-CD and run > sudo gparted.
resize your windows partition so you have at least a 30GB partition for Ubuntu.
Reboot to the Live-CD and then you can try installing Ubuntu.

NOTE- If you install wrong in the partitioning part you will loose windows!!!!

---

### Post by davidjmayo on 2007-07-12
Also defragment your windows partitions (a few times each) BEFORE resizing them or you may corrupt them.

---

### Post by gazzadtfan on 2007-07-15
Hi Folks

I may have been misleading in my last message. I'll try and simplify things if I can. 

I have one hard drive (250Gb) divided into four partitions. 137gb, 40gb, 40gb and 33gb. I wanted to keep the smaller partitions untouched and install Ubuntu and XP on the largest partiton thus making further partitions for XP, Ubuntu, home, and swap. This would make 7 partitions in total. 

My machine is slightly older now and when I first installed the new hard drive, it only recognised the first 137Gb. Something to do with large drive recognition which mine didn't have but since I made further partitions I can at least back data up etc to these smaller partitions. I'm not bothered if Ubuntu is able to 'see' them.

I thought dual installing would just work the same as if the 137Gb was my whole hard drive if I made more partitions to cover everything. Or have I totally missed something here?


gazzadtfan

---

### Post by ReaderRat on 2007-07-15
As alienexplorers said - You will need to resize (shrink) the 137 GB partition to make room for your Ubuntu partitions.

---

### Post by testube_babies on 2007-07-15
> **gazzadtfan said:**
> I have one hard drive (250Gb) divided into four partitions. 137gb, 40gb, 40gb and 33gb. I wanted to keep the smaller partitions untouched and install Ubuntu and XP on the largest partiton thus making further partitions for XP, Ubuntu, home, and swap. This would make 7 partitions in total.

You will run into one big problem:
1)  One hard drive can have at most 4 primary (logical) partitions.  I'm assuming all four of your current partitions are primary.

Other key factors to consider:
2)  Ubuntu cannot be installed on an NTFS or FAT32 file system; therefore it can't be installed on the same partition as Windows.
3)  Ubuntu needs 2 partitions:  1 for the OS and one for swap space.  It is possible to install without a swap partition, but is not recommended.

So, here's how the hard drive will look if you want to install Ubuntu, which would necessarily change your partitioning scheme:

(Partition - Filesystem - Usage)
0 - NTFS - Windows
1 - ext3 - Ubuntu
2 - linux-swap - Swap
3 - ??? - extra data

---

### Post by freebird54 on 2007-07-15
If you can back up one of your 'extra' partitions completely, you can delete it, then create an extended partition instead.  Within THAT, you can create more partitions as needed.  So

1. Defrag main partition, then shrink it
2. Delete the backed up partition.
3. Move partitions as needed to have the empty spaces next to each other.
4. Create extended partition in entire empty space.
5. Re-create the backup partition WITHIN the extended partition
6. Install Ubuntu using remaining empty space (within the extended partition again - Ubuntu won't care)

WHEW!

Ok - that all make snese?

Incidentally, many systems can  pick up the larger HD's after a BIOS update.  Have you investigated this?  It can simplify things if LBA mode works right...!

---

### Post by gazzadtfan on 2007-07-16
Thanks freebird54

I'll look at what you suggest. It all makes sense. How would suggest I shrink the partition? Would I use gparted or something along those lines?

gazzadtfan

---

### Post by freebird54 on 2007-07-16
Yup - GPartEd does it fine.  I have seen faster implementations of the functions, but it works very well.  Easiest is to fire up a Livr CD session, and grab System->Administration->Gnome Partition editor from there...

---

