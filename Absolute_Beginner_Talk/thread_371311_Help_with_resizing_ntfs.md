---
title: "Help with resizing ntfs"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by swa2b41 on 2007-02-26
Hello again,
I am running the Ubuntu live cd and want to install along with xp was recommended in an earlier post that said, "To dual-boot - first defragment XP and run a disc-scan. Then (once you've run the 'check disc' option in the LiveCD menu) - use the Live CD (System/Administration/Gparted) to resize XP (ie shrink it) then double click install option on desktop - select 'use largest available free space' option - and it will do the rest for you).
 So I went to administration Gnome Partition editor and it is open now I have no clue what to o before I try to install!!! Thanks for the help... If it helps it says:
/dev/hdal  ntfs  18.65 Gib 12.46 Gib   6.19 Gib boot

Jen...

Also wasn't sure if I should have continued this in the previous thread or start a new one...

---

### Post by NewOldTimer on 2007-02-26
check this...[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Kateikyoushi on 2007-02-26
I would recommend you to read this guide this explains the installation procedure. [LINK]("http://www.psychocats.net/ubuntu/installing")

You need to make 2 more partitions a bigger one ext3 which hould be mounted as / and a 1 GB one as swap.

---

### Post by mikewhatever on 2007-02-26
You just right click on the partition you want to resize, choose resize from the dropdown menu and either choose the size or drag from the end left. Do not resize too much, because you only have 6 GB of free space.

---

### Post by swa2b41 on 2007-02-26
thanks bunches again... I am up and running... Yipee, yahoo, way cool!!!

---

