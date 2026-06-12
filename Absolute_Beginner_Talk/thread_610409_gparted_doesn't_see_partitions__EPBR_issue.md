---
title: "gparted doesn't see partitions / EPBR issue?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by antonym on 2007-11-11
none of the previous threads about this issue ended conclusively, and I've got a bit of extra info, so I think this merits a fresh thread.

ok, so there's something odd about one of my hard drives, but no amount of searching google has turned up anything useful at all. 
there are two symptoms: 

one -- gparted in ubuntu displays one of my hard drives as just unpartitioned space, despite the fact that there are five partitions on it. fdisk, on the other hand, displays them correctly, and they are also properly mounted.

two -- partition magic, under windows, gives me the same odd error message every time I start it: it "has detected error 111 on the partition in sector X" (which I've deduced is located on the last partition on the disk). it then says "The contents of the extended partition boot record are in the wrong order. Norton Partition Magic can fix this problem by reordering the EPBR entries correctly." Except of course it doesn't, because it always gives me that error.
I also recently tried to merge two of the partitions (in PM), because one is empty and I don't need it, and everything seemed fine until I restarted, and it gave me an even more obscure "error 1529 while executing batch", which I've been unable to find anything useful about... at least not in the english language.

so, clearly something is up, and I think these two issues are related. 
It's occurred to me to try to just format the partition that the error was detected in, and see if that clears things up, but I'd rather not do that if I can solve the problem some other way.

primarily, I'd like gparted to see the partitions on that hard drive, because I wanted to do a fresh install of ubuntu.... I only mention the EPBR thing because it might be relevant to that goal.

---

### Post by bornskilled200 on 2007-11-12
I seem to have a problem that is sort of like yours. This is incredibly annoying but my gparted(partition editor GUI) crashes when i refreh all devices...
Hope this is fixed.

---

