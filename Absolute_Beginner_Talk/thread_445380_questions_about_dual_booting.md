---
title: "questions about dual booting"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by tmenyc on 2007-05-15
I've read the community listing about dual booting, and most of it makes sense.  However, I have never resized a partition or made a swap partition.  I have a 160g hdd, with about 70 g available in the ntfs partition and another 7 or so in a fa32 partition.
1. do I first shrink the ntfs partition to create unallocated space, then assign that unallocated space to the fat32 partition for ubuntu to use?
2. how do i make a swap partition?

TIA

Tim

---

### Post by Nekiruhs on 2007-05-15
The live Cd will have a resize and install option for you to use. Just use that,
And I'd recommend using ext3 note FAT32

---

### Post by icechen1 on 2007-05-15
> **Nekiruhs said:**
> The live Cd will have a resize and install option for you to use. Just use that,

But BACKUP DATA first!

---

### Post by foxmulder881 on 2007-05-15
The best way would be to shrink the NTFS partition to your preferred size. Then completely erase all your other partitions and let the Ubuntu Installer do all the rest for you. Don't try and run Ubuntu off FAT32.

All of the above you can do with the GParted LiveCD.

---

### Post by reidms on 2007-05-15
Yes- the installer can do it for you- but be careful to review the changes before making them, and of course back up your wanted data just incase of a problem

---

### Post by krisfrajer on 2007-05-15
resizing a windows partitions can be a little unpredictable. I will recommend to run defrag first... then to create a solid backUP (worth to repeat and emphasize) and cross your fingers. If by any chance you lost files during the shrinking process or even damage the software then you can find some posts here in the forum how to try to recover the data... but then again, you will not have to run into that because you already have backups (don't you?)

---

### Post by trak87 on 2007-05-15
> **tmenyc said:**
> 1. do I first shrink the ntfs partition to create unallocated space,

Yes.

> then assign that unallocated space to the fat32 partition for ubuntu to use?

Yes, but don't use fat32. Use ext3. Fat32 is a Microsoft thing. Linux can read/write to it but you don't install the Linux OS itself to it. People generally use fat32 as a common drive between the two operating systems, but not to install Linux on.

> 2. how do i make a swap partition?

You do this during the Ubuntu installation. Select the manual partitioning option during the install, otherwise you can easily/inadvertantly wipe out the Windows partition. When you get to that point you simply tell it to make a swap partition and give it a size (generally double the amount of RAM installed).

---

### Post by foxmulder881 on 2007-05-15
> **krisfrajer said:**
> resizing a windows partitions can be a little unpredictable. I will recommend to run defrag first... then to create a solid backUP (worth to repeat and emphasize) and cross your fingers. If by any chance you lost files during the shrinking process or even damage the software then you can find some posts here in the forum how to try to recover the data... but then again, you will not have to run into that because you already have backups (don't you?)

Defragging first is good advice.

Everyone always says that partition resizing is risky, yet in my 10+ years of IT experience, I've never had any problems yet. Which is why I happily recommend it.

---

### Post by tmenyc on 2007-05-15
wow, thank you for the great advice -- so, to summarize:  I have already backed up and defragged.  I run the install on manual, shrink the ntfs by some 20 gb, delete the fat32 (3602 MB, 3200 MB used), and follow the instructions or let it run the rest of the way?

---

### Post by foxmulder881 on 2007-05-15
Spot on champ!

---

### Post by alienexplorers on 2007-05-15
The only thing I would add is to make a /home file along with / and swap.

---

### Post by krisfrajer on 2007-05-15
Just resize the hard drive and you do not need to erase anything. Load the live ubuntu cd and then run install ubuntu and then during the installation ubuntu will allow you to choose your partition to install linux and it will itself do the reformatting.

---

### Post by trak87 on 2007-05-15
Creating a separate /home partition is good advice. That way, when it's time to upgrade to the next Ubuntu, you can reformat the main system partition while leaving the /home partition untouched.

---

### Post by tmenyc on 2007-05-15
how big should /home be?  Is there an ideal size?

thanks!

---

### Post by alienexplorers on 2007-05-15
The /home partition can be whatever size you like.  I use it for storing data & pictures so mine is quite large.

Root  15GB
/home  40GB
swap  1-2gb

---

### Post by tmenyc on 2007-05-15
ah...looking at the data at the bottom of your post, the root you built is where ubuntu is, and /home is where you keep your data?
thanks

---

### Post by spyker3292 on 2007-05-15
I use a gparted live cd for all my partition stuff. The live cd works fine for it too. (It's suprisingly easy and I haven't had any partition problems yet)

---

### Post by tmenyc on 2007-05-16
OK, I'm back.  I was able to shrink the ntfs partition easily enough, which created 19995 MB free space.  I could create the swap also, but when I did so , that rendered the remaining space unusable and I couldn't set up the root partition.  
Even so, there was no selection for "root" or "/" available to me.  So I aborted.
What am I missing?

Thanks!

---

