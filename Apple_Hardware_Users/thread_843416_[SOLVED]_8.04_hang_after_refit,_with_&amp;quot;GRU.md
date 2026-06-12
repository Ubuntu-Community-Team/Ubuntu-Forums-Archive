---
title: "[SOLVED] 8.04 hang after refit, with &amp;quot;GRUB&amp;quot; after fresh install"
date: 2008-06-28
forum: Apple Hardware Users
---

### Post by flurios on 2008-06-28
Hey there, I installed kubuntu 8.04 (next to osx) on my macbook pro. I had ubuntu there before, so no need to repartition... but my kubuntu does not boot. it hangs with a black screen and "GRUB" after I choose linux in refit.

Maybe it is because I chose not to install a bootmanager in the last step of the installation process? how can I fix that? The dvd booted just fine and I did not encounter any errors during install. refit did not need to be synced...

cheers

---

### Post by flurios on 2008-06-28
I installed kubuntu again, this time with bootmanager on (hd0,2), I also tried [this]("http://ubuntuforums.org/showpost.php?p=3303463&postcount=11"), but it didn't change anything... except that I have two linux boot entries in refit now... both hang with "GRUB" and a flashing cursor "_" 

the refit tables look like this:

> 
GPT
# Start End Type
1 40 409639 EFI System (FAT)
2 xx xxxxxx Mac OS X HFS+ 
3 xx xxxxxx EFI System (FAT)
4 xx xxxxxx Linux Swap

MBR
#A Start End Type
1  1 409639 EE EFI System Protected
2  x xxxxxx AF Mac OS X HFS+
3* x xxxxxx 83 Linux
4  x xxxxxx 82 Swap


---

### Post by liberalist on 2008-06-28
I will try to help you, flurios. I have an iMac (5.1 generation for insiders, 17inch) and have had numerous 'problems'. There are definitely hacks and the like, but it is better to search in Kubuntu specific documentation.

Known issues
0. Google frequently does: kubuntu, do you mean ubuntu? 
1. Ubuntu docs can be applied to Kubuntu and the other way around.
2. Kubuntu is 'officialy' not 8.04 LTS. 

In free time, I try to help Mac users as much as possible on a 'Bettified' forum (which is still in "beta, la fea" stage). I am now resolving an Opera specific problem in the 'old' stable release of my favorite GPL forum.
"Commercial" address: kubuntupedia.com (not linkified for several reasons)

---

### Post by cyberdork33 on 2008-06-29
you seem to have the EFI flag on two different partitions for some reason.

---

### Post by flurios on 2008-06-29
alright, I used a gparted bootable cd to delete the old linux and swap partitions. then I installed kubuntu fresh from dvd. created a new partition for kubuntu and swap -- kubuntuwise everything works fine, without even resyncing refit.

I have no clue, why it didn't work out using the old partitions...

cheers

---

### Post by flurios on 2008-06-29
solved... but now the topic looks a bit messed up ... what happened to the """?

---

### Post by rjcalifornia on 2009-09-05
So, can I use the Kubuntu CD installer partitioner to delete the old partitions?

---

