---
title: "Accessing Music Files from XP HDD"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by dmg025 on 2007-03-14
**I currently have a 250 GB HDD (170 gb free) with Windows XP and a 160 GB HDD (150 gb free) with ubuntu.  I am obviously dual booting and everyting works fine except for one thing.  I want to play my music on both systems and I am not sure what the easiest method is.  Here are my ideas, let me know if anyone things they could work**
[I]
1)  Update my ipod with XP, then use a program in Linux and stream/upload music from my ipod (I will need to do this every time i download new music)

2)  Access my windows files while in Ubuntu (no idea how, maybe some drivers?  might be risky?)

3)  Copy all of the files from XP to Ubuntu (not efficient because I download new music every day)

4)  Partition my winows hard drive into some other format and put music in that  partition (I have no XP reinstall cd, so I don't think this is gona happen)[/I]


Thanks in advance if anyone can help me,

DMG

---

### Post by Belyel on 2007-03-14
You can easily do both #2 and #4 on your list. For accessing your windows files, it is easy to read from ntfs, and you should either search the forums or look at the quick start guide for Ubuntu to figure out how to do that.  I'd tell you here, but I don't remember the exact steps.

#4 is a great method if you want to be able to share data between windows and ubuntu.  YOu can format a portion of your drive to Fat32, which both windows and ubuntu recognize and read/write just fine.  It looks like you have plenty of free space on your drives, so you could even make multiple partitions.  The easy way to do this is to go into windows, defrag your drive, then boot either from the gParted liveCD (do a google search) and use its GUI to resize your ntfs (windows) partition and make a new fat32 partition or partitions, or you can install gparted or qtpart from the repositories (do a search in synaptic) and resize them from inside LInux.  Make sure you defrag first!  And back up any important data.  The resize works probably 95% of the time, but you don't want to lose something important like your thesis or pictures.

---

### Post by airencracken on 2007-03-14
This should help you accomplish #2

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

It's sort of a quick and dirty fstab edit, but it works well enough.

---

### Post by dmg025 on 2007-03-14
Ah, thanks guys, I appreciate the fast response.  I think I am going to try and partition that windows driver first as mentioned and put it in a fat32 format.  Now i just need to go buy some cd's so i can make a g'parted cd

If that doesn't work then I will try the other advice.  I appreciate it.

DMG

---

### Post by _samba_ on 2007-03-14
> **airencracken said:**
> This should help you accomplish #2

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

It's sort of a quick and dirty fstab edit, but it works well enough.

This one works like a charm. 
... and you'll have it mounted every time you boot your ubuntu.

---

### Post by djgrandmarquis on 2007-03-14
I have a similar situation: an external disk that must be accessible to both windoze and kubuntu. So I formatted it as ext3 and installed a windows driver to read/write it (Linux supports ext3 by default, of course).

You too could install the driver in windows, and write new music directly to your ubuntu partition.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

