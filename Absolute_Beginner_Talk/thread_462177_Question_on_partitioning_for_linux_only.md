---
title: "Question on partitioning for linux only"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by linfidel on 2007-06-02
I want to upgrade my Ubuntu system with a new motherboard, more memory, maybe a new hard drive, etc.

I've installed so many different distros (and some multiple times, of course), and I'm getting tired of redoing everything, so I want to make separate partitions for /home, and possibly for partitions with global program settings.

If I have existing partitions, will the installation handle mounting them correctly, or do I have to do that myself?  And if I have existing partitions for ones other than /home (/etc ?), will it write to it without overwriting config files, or should I forget about that?

I'd like to get an idea of what I need to do beforehand, so I can decide on a strategy that's not too complicated, but minimize the drudgery.

I've tried making separate partitions in the past, but then the installation got complicated, and I didn't really know what to do, so I always backed out and took the easy way.

Thanks for any tips you can come up with.  I'm not a total newbie, but I'm fairly new at the administration part.

---

### Post by plcdfa on 2007-06-02
/home can be on a separate partition, so all your personal setting and data are kept over new installs. All you have to do in the ubuntu installer to set the partition's mount point to /home and not get it formatted. (It surely can be done with other Linux installers too.) This way none of your stuff will get deleted or overwritten in your home directory. Global setting reside in /etc but I don't think it can live on it's own partition. Also, sharing global setting over multiple distros or releases could be dangerous cos this way different versions of the same program would read and write the same config file. It might also cause minor problems with your personal settings in your home folder, but not very likely.

---

### Post by linfidel on 2007-06-02
> **plcdfa said:**
> /home can be on a separate partition, so all your personal setting and data are kept over new installs. All you have to do in the ubuntu installer to set the partition's mount point to /home and not get it formatted. (It surely can be done with other Linux installers too.) This way none of your stuff will get deleted or overwritten in your home directory. Global setting reside in /etc but I don't think it can live on it's own partition. Also, sharing global setting over multiple distros or releases could be dangerous cos this way different versions of the same program would read and write the same config file. It might also cause minor problems with your personal settings in your home folder, but not very likely.Thanks.  I wouldn't try to share /etc with other distros; I was thinking about for reinstalling the same one, or possibly upgrading.  But perhaps it would be better to just backup settings, in case I need to remember what I did, or to cut and paste into the new file.

Meanwhile, I just got back from Fry's with a new motherboard/CPU combo (AMD dual-core 5600) and 2 GB of RAM.  No good deals on drives, so that will wait.  Bad timing though, in that it was a bit crowded, and then the computer system went out, and it took somewhere near an hour just to get checked out (manually).

Oh, well.  Onward and upward, I suppose.  If nobody hears from me for a while, things didn't go well.  :)

---

### Post by plcdfa on 2007-06-03
Well, if you use the dist-upgrade method when a new Ubuntu version comes out then you'll keep your settings in /etc and everything else as well. I prefer a clean reinstall tough, it seems more reliable for me and I have my home  dir on a separate partition anyway.

---

