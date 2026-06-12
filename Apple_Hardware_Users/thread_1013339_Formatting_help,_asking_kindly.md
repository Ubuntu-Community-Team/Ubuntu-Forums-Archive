---
title: "Formatting help, asking kindly?"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by macyattacky on 2008-12-16
Hey guys, I've got a bit of a problem I was hoping you could help with. I've got the first generation macbook and had Xp installed via bootcamp. A friend got me to try ubuntu, which made it's partion and linux swap on the Xp partition. This did something to the Xp to make it unbootable, so I formatted the Xp partition and ubuntu partion back into hstf+. However, before bootcamp assisstent will let me recombine everything into one drive, i need to get the linux swap into fat32 or something so I can format it back into hstf+.  

I've got the ubuntu disk I can boot off of, so guys how does one go about formatting the linux swap into something Osx can handle?

ps. I can get back with the system specifics if they're necessary

---

### Post by chrisamiller on 2008-12-16
Without going into details, if you boot from the Ubuntu Live CD, you can use gparted to do your formatting.

I can't remember if it's installed by default, but 'sudo apt-get install gparted' will grab it for you.  Use 'sudo gparted' to run it.

---

### Post by nordmichael29 on 2008-12-16
The above post by chrisamiller is good, gparted is installed by default on hte live CD. you can access it by opening a terminal and typing in "sudo gparted" from gparted you have to unmount the swap drive, and the remove the partition, or perhaps you can convert it I don't know for sure.

---

### Post by damis648 on 2008-12-16
First off, the filesystem is called HFS+. 

If I understand correctly, you just need to reformat the Swap partition to FAT32 so that the OS X disk utility can reformat it to HFS+ and then combine all partitions into one? OS X's disk utility can format it. Fire it up, click the swap partition, go to the "Erase" section and set the filesystem as HFS+ and erase.

---

### Post by cyberdork33 on 2008-12-17
> **damis648 said:**
> First off, the filesystem is called HFS+. 

If I understand correctly, you just need to reformat the Swap partition to FAT32 so that the OS X disk utility can reformat it to HFS+ and then combine all partitions into one? OS X's disk utility can format it. Fire it up, click the swap partition, go to the "Erase" section and set the filesystem as HFS+ and erase.
but you might need to run it from the installation dvd in order to modify the startup disk.

P.S. Bootcamp will not work if you have more than one windows partition either. You need to stick with DiskUtility.

P.P.S. In the future, just post here, and maybe we can help you fix your system without you having to wipe everything out first.

---

