---
title: "How do I turn free space into Fat32?"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2005-12-06
I've managed to free up space from NTFS partiktion, but now can't work out how to change it to Fat32.

---

### Post by Qrk on 2005-12-06
You can install gparted, which is in the repositories,

```
sudo apt-get install gparted
```

Or you could pop in the Live CD which includes gparted.

---

### Post by mdsmedia on 2005-12-06
I created the free space with QTParted...I can't work out how to make it Fat32.

---

### Post by mdsmedia on 2005-12-06
I think I've got it....I had to commit to the change to free space. Now just gotta work out the next step.

---

### Post by mdsmedia on 2005-12-06
No I thought I'd just missed a step, but having committed the change QTParted won't let me do anything else. I now have 7 gigs of free space that Parted says is Hidden. What's the next step to change it to Fat?

---

### Post by littlepr on 2005-12-06
Select the partition in qtparted, right click and selct create. Set partitiom type to fat32. Label it whatever you want. Once you hit ok and it says 100 % complete click on the save icon (Floppy icon) and it should be all set.

---

### Post by Herman on 2005-12-06
Or, in Windows XP go 'Start', 'Control Panel','Administrative tools','Computer Management','Disk Managment'.
Then right-click on the partition  you want formatted as FAT32 and click 'format', and then set the filesystem type in the middle feild from NTFS to FAT32 and click 'Okay'.:p

---

### Post by djh3 on 2005-12-20
[QUOTE=mdsmedia]No I thought I'd just missed a step, but having committed the change QTParted won't let me do anything else. I now have 7 gigs of free space that Parted says is Hidden. What's the next step to change it to Fat?[/QUOTE]

I am at the same stage.  with QTParted I resized a Windows partition and deleted an ext2 partition that I no longer use.  Now both say they are "Hidden" and I can't seem to do anything with them.  What I really want to do is increase the size of the partition that I use for Ubuntu but I don't seem to be able to increase the size (notwithstanding that I now have 4 GB of free space).  Did you come across a solution to your problem?  Help--any body?

---

### Post by mdsmedia on 2005-12-20
I exited qtparted...went the windows route and formatted the space FAT32.

I then moved data off windows partition into FAT32. Didn't have enough room in FAT32 for all data, so went back to qtparted to resize NTFS again (with more freed up space as data had been moved). 

Same problem....resized NTFS with qtparted, then it wouldn't allow me to do anything with the free space. OK, I thought, let's go the windows route again. I'd messed up my MBR...couldn't load GRUB. 

Ended up reinstalling Linux in the free space....now I'm attempting to get everything over from the old Linux partition to the new.....then will format that partition FAT32 and move data again.

Cross fingers :)

---

