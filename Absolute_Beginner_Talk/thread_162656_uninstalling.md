---
title: "uninstalling"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by patanjali on 2006-04-19
I am currently multi-booting a laptop with Ubuntu, Kubuntu, and xp.  My question is, howcan I get Ubuntu to take over the space that is currently occupied by Kubuntu?  When I look at the laptop disk, Ubuntu can see xp, but doesn't list Kubuntu.

Hope someone can help.

Patanjali.  :rolleyes:

---

### Post by macdo on 2006-04-19
I am assuming that you installed Ubuntu and Kubuntu from different disks, and that you didn't just install kubuntu-desktop from synaptic... 

The tool you need is called gparted: install it from synaptic.
Then press alt+F2 and type gksudo gparted
BE CAREFUL! This is a very powerful tool.

Before you start, go to System->Administration->Disks, and look for a partition that isn't mounted but is not Windows (It doesn't have a windows file system - either FAT32 or NTFS, and the status is "inaccessible". Get the partition name (at a guess, it will be hda2 or hda3).

Delete your Kubuntu partition with gparted, and make a new partition with the empty space, that you will format as ext3 (FAT32 if you want to be able to access it from Windows). Remember the name of the new partition...

Once you're sure that you've got it all right (and there is no going back, so be SURE...), apply your changes with the Apply button.

Reopen the Disks Manager, and enable the partition that you've just created. Before you do that, you'll need to create a folder to mount it at - something like /mnt/newpartition. Browse for that folder at the access path box.

And you should be done.

I cannot stress too highly the importance of getting things right before you format... if you format the wrong partition, you could easily erase Ubuntu, Ubuntu's swap file, or Windows.

Good luck.

---

### Post by patanjali on 2006-04-19
When I look at the partition list Ionly see the following:
Partition 1
Partition 2
Swap Partition
Partition 5

Partitions 1,2, and 5 are accessible, and Swap Partition just gives "635.32 MiB (Free space not available)".

Patanjali

---

### Post by macdo on 2006-04-21
Can you give me the mount points (like /, /home, and so on)?

---

