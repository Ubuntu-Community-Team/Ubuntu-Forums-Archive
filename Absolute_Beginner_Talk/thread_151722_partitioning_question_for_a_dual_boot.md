---
title: "partitioning question for a dual boot"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by uzi09 on 2006-03-28
hey all,

sorry for yet another dual boot question, but basically i'm going to be getting a new laptop soon and ofcourse the manufacturers have XP preinstalled on it. from what i've read about dual booting  (on the same disk) is that you must wipe out the whole hdd and reinstall both os's (specifically windows first because windows has some problem with partitions having linux or something or another - basically windows has yet another problem.) anyway, i was searching through the forums to try to find some answers for my question (about to come, just gimme a sec please) and came across a few threads that i understood saying we could just install ubuntu and partition the hdd with the utility provided, but it doesn't mention anything about formatting the hdd. is it possible to do that (i know partition magic is able to repartition a drive without having to remove the data, but i don't have that kinda money to spend - then again, i don't really have any money to spend after buying the laptop). 

secondly, as far as partitioning goes, if i were to stick with just windows, i would have had a partition with just windows on it and the rest of the disk have my data so that if windows starts acting up, i format that half and reinstall and i'm good to go. the thing is, i'd like to install linux on it (ultimately, i'd love to stick with linux only, but at the moment i'm still a newbie to it as well as i'm a gamer and i tried wine on my desktop but had major issues with it trying to run steam :S). the thing is, if i have 3 partitions (1 for windows, 1 for linux, and one for data) i'm going to have to mount the data partition onto linux whenever i need to access data and as far as it being organized, it's not going to be organzied as well as linux would do it. k, so if i decide to stick with storing data on linux only (which is going to be REALLY difficult because if i'm using windows and want to save something, i don't know wth i'll have to do to get it to go to the proper place). also, one problem i've noticed on my desktop (which has 2 hdd's on it, one with windows and the other with linux), after installing ubuntu on the second disk, windows doesn't really see it. well, actually, it does see it, but when you try to double click the drive, it says the drive is empty (the same message you get when you try to open up D: without a cd in the cd-rom). i'm assuming this is because of the format ubuntu put on by default when it was installed. i believe this is the ext2 format (or something like that). i've also read that linux supports FAT32 as well and i know windows supports it too. is it possible to install ubuntu using the FAT32 format and still be able to access files through windows??

so basically, thats my lil dilemma. sorry for it being so long, but again here is a summary:

1) can we partition and install linux without having to format the hdd (and without using partition magic)

2) what is the best way to store data in a dual booted system so that either os can access it (but preferbally have it organized really well - as if you were just using linux).

any help is much appreciated
uzi

---

### Post by Princey on 2006-03-28
Here's what to do as I'm guessing you read the various posts about partitioning and mounting your drives. There's no need to reformat your drive especially if you bought a new laptop and doesn't have the Windows Disk. Here's what you can do.

1. With the hard drive with windows, pop the Ubuntu CD in and type install.
2. Chose the option to shrink windows [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")
3. Chose guided partioning. There, you can have a swap and root partition for linux and an extra FAT32 partition where you can save files both under linux and windows. **I strongly advise that you do not install Linux on a FAT32 partition. With windows running, viruses and even accidental deletion of files on that partition can pretty much leave you weeks trying to get back on track**

This way, you'll end up with hda1 (Windows), hda2 (ext)[That's your logical drive split into several partitions] hda5 swap, hda6, root hda7 FAT32. Now, all you'd have to do is to mount the drives. Here's the know how [http://www.ubuntuforums.org/showpost.php?p=846579&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=846579&postcount=8")

Good luck and don't be afraid to ask for help if you get stuck.

---

### Post by gunderwood on 2006-03-28
Your best bet is to re-size the the windows partition and create 2 additional partitions. I believe the ubuntu install CD will allow you to resize your Windows partition, and if not there are GNU tools such as GNU Parted  [http://www.gnu.org/software/parted/](http://www.gnu.org/software/parted/) and NTFS Resize [http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html) that will allow you to resize the window partiton. You can boot with a live cd and use the tools that way if you need to.

I would use a partion scheme something like this

hda1 -> windows
hda2 -> swap (2 times your ammount of RAM)
hda3 -> / (root ubuntu install) ext3
hda4 -> /home        ext3

Then I would install a ext3 driver for windows so you can use your home directory as a data directory shared between your OS's.

I'm not 100% sure what the state of ext3 drivers for windows is. But I know read access is fine, and last year I used some drivers that allowed decent write access (little slow, but reliable). Unfortunately I can't remember where I found the driver, but google is your friend or maybe someone around here knows.

The reason I recomend usint ext3 as opposed to a FAT32 file system is because FAT doesn't support permissions, users, groups ... therefore is insecure and doesn't support stuff like indexing.

Best of Luck

Greg

---

### Post by uzi09 on 2006-03-28
Thanks a lot guys. This is exactly what I was looking for (lol, i feel like i could have reworded it a lil better now =\).

Thanks again,
uzi

---

### Post by shawnhcorey on 2006-03-28
I have recently install dual boot on my Mac. You can read about it here [https://wiki.ubuntu.com/Shawnhcorey](https://wiki.ubuntu.com/Shawnhcorey)

Try to do all the calculations for your partitions before you begin. That is, calculate the start, end, and size; both in GB and MB. Remember: 1 GB = 1024 MB.

And then, have a good calculator with you when you install, just in case.

sc

---

