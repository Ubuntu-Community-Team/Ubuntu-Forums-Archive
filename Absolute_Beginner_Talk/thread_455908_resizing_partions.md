---
title: "resizing partions"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Sky Shark on 2007-05-27
RIght after fiesty fawn came out I decided to make my system dual book and split the harddrive almost completely in half between the windows and linux partition with the rest going to the swap file.  Now I've noticed I need more room on my windows partion than I do on my linux partion.  Is there anyway I can edit these two partions without having to lose all my data on either one?  If someone could help me I would appreciate it greatly.

---

### Post by hyper_ch on 2007-05-27
hmmm, you can use the desktop cd to boot ubuntu and then us gparted within the desktop cd to shrink your linux installation... and enlarge your windows one... however MAKE BACKUPS BEFORE MESSING WITH YOUR PARTITIONS.... it happens sometimes that something goes wrong and then you may loose all the data...

---

### Post by Sky Shark on 2007-05-27
> **hyper_ch said:**
> hmmm, you can use the desktop cd to boot ubuntu and then us gparted within the desktop cd to shrink your linux installation... and enlarge your windows one... however MAKE BACKUPS BEFORE MESSING WITH YOUR PARTITIONS.... it happens sometimes that something goes wrong and then you may loose all the data...

So when shrinking the linux and enlarging the windows, the only one i need to worry about is the linux one?

---

### Post by hyper_ch on 2007-05-27
no, you need to worry about all partitions on that harddisk... (except for swap....)

---

### Post by Sky Shark on 2007-05-27
> **hyper_ch said:**
> no, you need to worry about all partitions on that harddisk... (except for swap....)

Oh okay, btw is it highly likely that some thing will go wrong or one of those rare things that you prepare for anyways?

---

### Post by hyper_ch on 2007-05-27
well, it never happened to me (except for the one time where I chose the wrong partiton to be deleted... but that's not to blame on the partitioning itself).... however others had problems... it is recommended to defrag the windows partitoin at least twice before you want to alter anything...

for making the linux partition smaller I would use gparted... for handling the ntfs partitions I have always used Partition Magic in windows...

---

### Post by Sky Shark on 2007-05-27
> **hyper_ch said:**
> well, it never happened to me (except for the one time where I chose the wrong partiton to be deleted... but that's not to blame on the partitioning itself).... however others had problems... it is recommended to defrag the windows partitoin at least twice before you want to alter anything...

for making the linux partition smaller I would use gparted... for handling the ntfs partitions I have always used Partition Magic in windows...
Okay, thanks for you help dude.  BTW you wouldn't happen to know if I could make my windows partition read and write to my linux one?  If i could then I would just install stuff through windows but on the linux partition thus avoiding the possibility of screwing up a resize of the partion.

---

### Post by hyper_ch on 2007-05-27
You can read/write to ext3 partitions... you need to get the ext2/3 drivers for linux... a couple of thread further down there is the link and stuff...

---

