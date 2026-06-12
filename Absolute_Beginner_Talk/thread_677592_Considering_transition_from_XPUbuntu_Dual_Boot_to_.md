---
title: "Considering transition from XP/Ubuntu Dual Boot to Ubuntu only"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by areayetee on 2008-01-25
Ive been using Ubuntu Gutsy for a couple of months now. I successfully set up my Dell Vostro as a dual boot XP Home / Ubuntu System. Ive become extremely comfortable with getting everything i need done in Ubuntu.  Now I'm rarely booting to the XP partion. I'm wondering is there is a safe way to transition my "dual boot" into a "Ubuntu  only"system without losing my Ubuntu data or having to re-partion and start from square one?

---

### Post by chewearn on 2008-01-25
First, unless there is an urgent shortage of disk space, why not leave windows lying there, just in case?  I'm not for or against windows, but it's nice to have a back-up for comparison when things don't go right.

Second, if you are sure about removing windows, then a simple windows partition + grub menu delete will take care of it.

Then to recover the deleted space, easiest way is to create a new partition in it's place to store data.  A more complicated way involved booting to a livecd, umount all partitions, then rearrange things to your desire.

---

### Post by hyper_ch on 2008-01-25
well, I tend to agree... if it's not for needed-diskspace reasons I'd let windows stay...

---

### Post by ugm6hr on 2008-01-25
If you do need the HD space - why not use the entire XP partition as /home?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Obviously you would not need to resize any partitions - just reformat the Windows partition to ext3 and then start from "Using the new partition"

---

