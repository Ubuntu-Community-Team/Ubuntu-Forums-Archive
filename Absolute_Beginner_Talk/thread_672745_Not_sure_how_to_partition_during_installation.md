---
title: "Not sure how to partition during installation"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Aloshi on 2008-01-19
I'm new to Ubuntu and Linux (spent like 3 hours trying to get the darn thing to boot live).  So I ran the installation, and I've never even touched partitions before.  I understand what Partitions are but it seems to read my hard drive wrong. It says that I only have about 8 MiB of free space when I really have about 21.9 GiB.  I also have some weird alert sign on a partition that takes up about 7/8ths of my hard drive for some reason and the space remaining is a dash.  I clicked on information and it tells me to use something called ntfsclone and use the rescue function, and I have no idea what that means.  I plan to dual-boot XP and Ubuntu.  Any way to fix this?

Some info about my Hard drive:
It has about 80 GiB total.
It has about 21.9 GiB remaining.
XP is installed on it.
I have never touched the partitions on it, but I know there are 3 of them (two are small, one is huge).

---

### Post by Fleece Flamingo on 2008-01-19
You most likely bought your computer pre-installed with windows. What they did was made a huge partition ONLY for windows use and that is why it days it is taking up so much space. You have 20 gigs left but only for use with windows.

In the live CD you can fix this, open up Gparted under the systems tab and you can resize your windows partition to create another one for linux

It is STRONGLY recommended to backup your partition existing windows first (I didn't and mines fine, if it's worth anything)

---

### Post by Aloshi on 2008-01-19
Stupid windows, continuously trying to take over the world...

---

### Post by Fleece Flamingo on 2008-01-19
LOL yeah, it might take a while to resize your windows partition. Took me about 1 hour but it all depends on how fast your hard drives rpms are.

---

### Post by Aloshi on 2008-01-19
It won't let me edit the partition at all, though...

:|

---

### Post by Fleece Flamingo on 2008-01-19
Really? It should let you resize it and then you drag the bar to make it smaller. You're using the live cd right? Your windows partition is the NTSF. You could try defragging your windows XP partition to free some space if you want.

---

### Post by Aloshi on 2008-01-20
It wont let me resize it in any way. At all. I do have an alert thing that says my Hard Drive is damaged and to run NTFS - rescue though, but I don't know what it's talking about. :|

---

### Post by Aloshi on 2008-01-20
Erm, could I please get a reply? :|

---

### Post by zabien1970 on 2008-01-20
You should slean up your HD first to free up room, defrag and such through windows

---

