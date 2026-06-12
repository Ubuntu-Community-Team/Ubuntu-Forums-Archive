---
title: "partition problems"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by hansning on 2007-02-19
edgy + win xp

hey, still having problems with ubuntu recognizing my partition, and being so new to linux, i have no idea how to go about this...

I made a ext2 drive in windows, but ubuntu doesn't "see" it.  i can find it using fdisk in terminal, but don't know how to continue.  i have no knowledge of using the terminal, so any help is greatly appreciated...

---

### Post by housam on 2007-02-19
> **hansning said:**
> edgy + win xp

hey, still having problems with ubuntu recognizing my partition, and being so new to linux, i have no idea how to go about this...

I made a ext2 drive in windows, but ubuntu doesn't "see" it.  i can find it using fdisk in terminal, but don't know how to continue.  i have no knowledge of using the terminal, so any help is greatly appreciated...

Try to use this guide :[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by hansning on 2007-02-19
Thanks, that page had tons of very useful information, but i couldn't resolve my problem...

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) was a better example of what i was doing.
i THINK it's inside nano where i start getting messed up...  it doesn't look quite the same as the diagram, explained by the howto that it's that i'm running edgy.

For example, it seems like adding

#/dev/hda4    /shared    ext2    defaults    0    0

wasn't the right way to go...


i need some kind of UUID=XXXXX........

help?

---

### Post by petri on 2007-02-19
Here's psychocats/aysius pal Herman who has a tons of information too and he writes something about UUID :) [http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

I by myself doesn't "own" Edgy so I don't have this problem but I hope that the link above can give you some guidance to go forward.

---

### Post by Herman on 2007-02-19
EDITED post. Petri has the best answer, I think I misinterpreted the problem. I will have to be more careful with my reading in future. Sorry everyone.
Regards, Herman

---

