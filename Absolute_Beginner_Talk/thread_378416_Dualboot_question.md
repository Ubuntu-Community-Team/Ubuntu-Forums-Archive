---
title: "Dualboot question"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Jhawk44 on 2007-03-07
How do I configure a dualboot with my already installed WinXp Pro?

---

### Post by chewearn on 2007-03-07
More info needed on your PC harddisks configuration to be able to give meaningful reply.  E.g. where have you installed ubuntu and windows, etc.

---

### Post by Sbarton on 2007-03-07
You could look at this site for dual booting as well!
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
regards

---

### Post by Jhawk44 on 2007-03-07
well, I have one drive, a 250gb Western Digital Caviar. I havent installed Ubuntu yet, but windows is on the drive in a NTFS partition that takes up the whole of the drive. is the the info you wanted? and that website says it is not for "desktop" only "alternate", I have the "desktop" ISO.

---

### Post by confused57 on 2007-03-07
This site also explains how:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Godmanliving on 2007-03-07
I have a triple boot setup with two hard drives, oem 80 gig hd with Winxp, and a 250 gig western digital with a 50/50 parition (one side for ubuntu, the other for vista).   I Loaded xp, defragmented the F: drive (my vista/linux drive) ran the check disk to fix any errors and used Gpart automatic settings with the slider deal to set the partition to 50%.  I had to run check disk in winxp to get vista to load properlly again.  Vista is NTFS and Linux is the Linux swap and whatever the other parition type that is standard is.(im a newb).  Everything loads and works just fine. (unless i do somthing insane like trying to install my ati drivers and beryl)  GRUb loads and lets me select either the newest linux kernel, the one I started with or the Windows Boot manager to choose XP or Vista.

---

### Post by chewearn on 2007-03-08
> **Jhawk44 said:**
> well, I have one drive, a 250gb Western Digital Caviar. I havent installed Ubuntu yet, but windows is on the drive in a NTFS partition that takes up the whole of the drive. is the the info you wanted? and that website says it is not for "desktop" only "alternate", I have the "desktop" ISO.

Here is what I would do:
1. Boot up to the LiveCD, see if the Gnome desktop is able to load, check network detected or not, whether ubuntu is "happily" running, without serious issue.

2. Use GParted to resize the Windows partition (either the GParted in the ubuntu LiveCD, or use the GParted LiveCD; whatever worked); or use a Windows program like Partition Magic.

Note: the Windows partition should be start from the beginning of the disk, up to whatever size you want; you can give something like 10GB for ubuntu.

Now you have a free (unallocated) space in your harddisk (from where Windows end till the end of disk).

3. 
 Boot up ubuntu liveCD again, once Gnome desktop is loaded, click on the install icon on the desktop.  Just follow the setup wizard; at the part on partitions, select option to install ubuntu in the largest continuous free space.

That's all.

---

