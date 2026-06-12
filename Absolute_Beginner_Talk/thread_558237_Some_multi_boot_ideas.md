---
title: "Some multi boot ideas"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Leed on 2007-09-23
Just some ideas that may inspire and maybe you know some extra tips for me ;)

I'm planing to get a New PC some time next year, I've fell in love with Ubuntu running on my Laptop and want it integrated in my Future home machine. But I also want other Systems, in Basic I have this in Mind (Optional in Brackets):

1. Ubuntu with Gnome & Compiz-Fusion &  Kiba-Dock
2. Windows Vista
(3. Windows XP)
(4. Max OS X, if it by some miracle runs on other machines than mac)

This will so far be no problem for me, but I want things running in a optimal way between operation systems, therefore I want to follow these ideas

- Windows should run on FAT32 Partitions, to make it fully accessible by Linux

- Windows Core must have it's own Partition (Approx. 10GB), this makes it easier to back up, if the Windows partition mucks up, the rest isn't gone.

- Windows Programs shall be installed on a separate Partition, if I can recover Windows core after a crash, they will still run, plus program settings aren't lost. If using XP on Partition 3 the may even be able to run from the same installation

- Files will be stored on a separate FAT32 Partition, The Windows "my documents" Folder and The Linux Home Folder shall be referred to this Disk. I want all my Data to be on one Disk, accessible from all OS. 

- Ubuntu shall also use the Fonts folder in Windows, makes it easier to have the same fonts on both systems

- Ubuntu shall have a main partition and a swap partition for itself. Unfortunately I'm not smart enough to divide programs from the system's core, so they'll remain on one partition if I don't find another solution. 

- Grub will be used as Boot manager (I like using graphics)

- I would also like to use Wine and VMWare, but I'm not sure if there is a good way to use multi boot systems and VMWare without using a lot of Disk space for each OS in VMWare. Win XP shall probably only run in VMWare if not possible as multi boot with the same installation. 


That makes at lease 5 Partitions, perhaps one more for Games.

I'm hoping to make this System as Hybrid as possible, have I forgotten anything? Anyone have more such ideas?

---

### Post by por100pre1 on 2007-09-23
Go Vista and Ubuntu. [Here's]("http://ubuntuforums.org/showpost.php?p=3412810&postcount=3") a simple way to install them. By then it'll be at least Gutsy so you'll have Compiz-Fusion installed by default and Kiba-Dock will likely be stable by then. You can only have 4 primary partitions, one of them should carry logical partitions: swap and the remaining desired partitions.

---

### Post by Skidpad on 2007-09-23
You've obviously thought out your plans, but I would question the decision to use a FAT32-based filesystem for your documents partition.   I realize what you are trying to do, but I think you would be better served by making your data partition ext3, and then using the ["fs-driver"]("http://www.fs-driver.org/") to allow Windows full read/write access to it.

By doing so, you eliminate any file size limitations (FAT32 is limited to 4GB - not good if you are doing any movies), and gain numerous other benefits.    [File System Wiki]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

Just my $.02 worth...:)

---

### Post by Leed on 2007-09-24
Thanx for the tips, got no experience with Vista yet, didn't think it'd be more complicated than XP

I put the fs-tool on my laptop to test, great thing, now I can access things in Windows, if I must. I will definitely put it on my new system, also I didn't know about the 4GB limitation.

---

### Post by startherepodcast on 2007-09-24
For me ubuntu  runs like a dream. OSX does too
I run a fujitsu siemens laptop

how could this be possible :)

---

### Post by Leed on 2007-10-03
Sounds fun... pitty there's no official way, from viewing how Steve Jobs handles his software he may one day launch some patch that breaks your System if it's not what he wants it to be, just as he did in the iFone

---

