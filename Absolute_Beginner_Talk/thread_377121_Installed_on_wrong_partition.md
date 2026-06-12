---
title: "Installed on wrong partition"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Baest on 2007-03-05
Hi,

When I installed Ubuntu I tried to allocate 30GB for the install, instead my XP now has 30GB!  Is there a way to delete Ubuntu and get XP back at my full hard drive volume and start all over again? Anyone have experience with Partition Commander (which I am considering as a solution)?  Any other info. would be greatly appreciated.  Thanks!

---

### Post by Ek0nomik on 2007-03-05
Let me try to understand:

You allocated space on a NTFS, EXT3, FAT32, and Swap?  And you accidentally gave the NTFS 30GB instead of the EXT3 30GB?

---

### Post by Baest on 2007-03-05
That's right (I think).  In computer management of XP it lists
three partitions.  One 83.52G, one 2.9G (swap I assume) and
28G NTFS.  At startup this shows:

Ubuntu, kernel 2.6 15-23-386
Ubuntu, kernel 2.6 15-23-386 (recovery mode)
Ubuntu, memtest86+
OTHER OS:
XP Home

I previously deleted the Ubuntu partitions to try to get XP back as
the primary boot drive... then nothing would boot.  Then I reinstalled
Ubuntu and restored it to my original problem state.

Thank you for your help.

---

### Post by Amenemhet on 2007-03-05
La oops!
First, can you still boot to the xp partition? Can you boot to the Ubuntu partition?
There isn't enough info yet for me to help much. 
I guess so if you acn see xp computer management. So, if you want to resize then yes, you can do so, if your XP pro you can do it in computer management itself, if it is Home edition you will need a third party utility, like partition magic or whatever, there are lots out there.

---

### Post by Ek0nomik on 2007-03-05
So you got everything working now?  If so, great!  If not, let me know what the issue is and I will **try** to help.

Cheers!

---

### Post by Baest on 2007-03-05
Yes, I have been able to boot from both partitions.  The problem is I need more than 28GB for my Windows partition and I'm running out of room.  Ec0n, would you agree the only solution is a third party software or do you have another idea?  Thanks guys.

---

### Post by Baest on 2007-03-05
Yes, I have been able to boot from both partitions.  The problem is I need more than 28GB for my Windows partition and I'm running out of room.  Ec0n, would you agree the only solution is a third party software or do you have another idea?  Thanks guys.

---

### Post by lamalex on 2007-03-05
boot into ubuntu and use gparted to resize the ntfs partition. or you could do partition magic if you wanted.

---

### Post by freebird54 on 2007-03-05
You can use a Windows partition manager if you want, but they are no better/different really than the one on your Live CD (potentially faster, but not better).

You want to boot the Live CD, then run the GPartEd partition manager, resize the large Ext3 partition smaller, then upsize the NTFS partition for XP.  Should not affect anything else.

Clearer?

BTW - you run from the Live CD because you cannot make changes to the drives you are running from (true of ANY partition manager) so you ruin from the CD.  Also - interestingly enough - the last version of Partition Magic I used booted Linux to run from.. :)

---

### Post by jimrz on 2007-03-05
> **Baest said:**
> That's right (I think).  In computer management of XP it lists
three partitions.  One 83.52G, one 2.9G (swap I assume) and
28G NTFS.  At startup this shows:

Ubuntu, kernel 2.6 15-23-386
Ubuntu, kernel 2.6 15-23-386 (recovery mode)
Ubuntu, memtest86+
OTHER OS:
XP Home

I previously deleted the Ubuntu partitions to try to get XP back as
the primary boot drive... then nothing would boot.  Then I reinstalled
Ubuntu and restored it to my original problem state.

Thank you for your help.

apparently, on install, you resized your ntfs to 28Gb and then used the remaining space for ubuntu. is this correct? 

if so, one idea would be to resize your ubuntu partition to about 30Gb or whatever size you like. then create an extended partition using the newly unallocated space. you could then add 1 or more different partitions within the extended partition to suit whatever your needs turn out to be. might even leave a fair bit unallocated until you decide how best to proceed.

i am not familiar with partition commander but either gparted from your live cd or partition magic can easily do this. i think gparted would be the better choice + you already have it. 

i would also suggest that you make a FAT32 part within the extended part. since both ubuntu and win can read/write FAT32 natively, you could use this partition to keep the files that you want to be able to work on from both os's, this would also free some space in your current ntfs part, as you move files from it to the new one.

---

### Post by Baest on 2007-03-16
Thank you guys for your help.  Sorry it took awhile to update you (I did have a computer, I've just been busy).  I used GParted to first get free space after my windows partition.  I ended up deleted Ubuntu [I]for now[I] and then I had to figure out how to change the MBR.  I couldn't really find anything out there that worked and then I realized I had a second XP boot disc that I had forgotten about.  (I couldn't find the original, but had another from a laptop - thankfully I could use it without being arrested and thrown on a pirate ship.)  Again, thanks for your help, I really appreciate it.

---

