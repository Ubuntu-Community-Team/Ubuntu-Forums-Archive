---
title: "Help going back to dual boot."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by xanous on 2007-05-26
I need to get windows back on my HD. I would like a dual boot but I formated my HD and only have one partition. Is there a way to create a partition on an existing Ubuntu installation. Something like Norton's Partition Magic for Linux would be great. I can't seem to find anything like that though. Am I going to have to reinstall Ubuntu to do this?

---

### Post by 4tro on 2007-05-26
try gparted ( sudo apt-get install gparted ), but that only works if you still have enough free space to accommodate a windows partition.

And you will have to reinstall grub on your MBR after you installed windows because windows blatantly decides you won't need the stuff on your other partitions.

You can use a grub live cd for that, but I don't know a direct link for that

---

### Post by xanous on 2007-05-26
Yep super grub disk works well. Will try gparted and post results. Thanks.

---

### Post by xanous on 2007-05-26
OK forgot I tried that before. All of the buttons are grayed out. I cannot resized/move, delete or make new. Nothing. It shows that I have 60 gigs of free space so I know thats not it. Any ideas?

---

### Post by xanous on 2007-05-26
OH found something. Has anyone tried the GParted live CD? Maybe that will work. I don't want to lose data though.

---

### Post by ugm6hr on 2007-05-26
> **xanous said:**
> OH found something. Has anyone tried the GParted live CD? Maybe that will work. I don't want to lose data though.

Yes it will work.  Unfortunately, no partitioning software is 100% reliable for data, but I didn't have any problems with it.  If you want to have Windows on NTFS - create an NTFS partition (primary rather than extended), but when you reinstall Windows, ask it to reformat it again, cos GParted is not great with NTFS yet.  Obviously, if you use fat32 it will make file sharing a little easier (i.e. no need to install ntfs-3g), but Windows will run slightly slower.  Other bit of advice - boot GParted LIveCD from option 2 - option1 seems not to work at all.

---

### Post by Cloudedbrains on 2007-05-26
Gparted needs to be run from the liveCD :)
Ive used it that way fine (with a few minor hassles) ;)

---

