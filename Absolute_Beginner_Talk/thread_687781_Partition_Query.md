---
title: "Partition Query"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Algus on 2008-02-04
Alright, please excuse me if this is the wrong forum.  I'd def consider myself an absolute beginner :P.  Alright, my notebook has a 60 GB HDD partitioned into 15/5/40 GB.  It's a Sony notebook so the 5 GB is "hidden" to be used as a recovery partition.

Anyway, I was using [this guide ]("http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu") to setup Ubuntu because I wasn't quite ready to sacrifice my Windows install.  I burned the Ubuntu 7.04 disc (Unfortunately it seems this guide is a bit out of date and directed me to 7.04 instead of 7.10...) 

Everything worked well enough, I was impressed that Ubuntu could support my wireless card and my battery display and everything worked right out of the box.  In fact as near as I could tell the only things that didn't work were my function key and start key.   I was very impressed.  

Here's my problem though.  When I went to shrink my 40 GB partition in order to install Ubuntu I planned to shrink my partition to 32 GB and leave 8 GB for Ubuntu.  I accidently reversed it though and left 8 GB on the drive and gave 32 GB to Ubuntu.  So my question is - how difficult would this be to fix? 

With my (limited) computer knowledge I would assume this would involve formatting the partitions and restoring it to the 40 GB NTFS partition it was before my Linux install (so I'd need to backup the stuff on my "new" 8 GB partition) which doesn't sound entirely unnattractive since it might give me a chance to install 7.10 instead.  

I do have [FS-Driver]("http://www.fs-driver.org/index.html") which someone on another forum I post at directed me to so if the process of doing this is too difficult I can "get by"  

Basically my question (multipart) is - how would I go about fixing my problem? Is there some sort of Windows program I could get to fix the partition in Windows? Is there a Ubuntu utility I could use? Would it be worth the trouble? When I'm interacting with my Ubuntu partition in Windows could I put files "anywhere" ? 

Thanks :D

---

### Post by LowSky on 2008-02-04
ubuntu's live cd comes with a program called Gparted (disk partitioner) it can resized partitions without have to reformate them.

---

### Post by Algus on 2008-02-04
Easy to use then? Alright, I'll get into the CD and check it out.  Can I basically "merge" the two partitions and then resize like that?

---

### Post by Algus on 2008-02-04
Well I, uh, couldn't find gpartition on the Ubuntu Live CD >.> but I ended up going to their website and downloading the ISO and burning it to a disc.  I just wanted to say that it worked great.  Took me a little bit to figure out how to use it but once I did it worked fine.  I shrank my Ubuntu partition to just under 8 GB and brought the extra space over to my Windows partition.  I should have plenty of storage space in Windows for any Windows aps I need to install in the future.  

I was really worried I was going to kind of be stuck so thanks a lot for pointing me in the right direction.  I really appreciate it.

---

