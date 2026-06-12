---
title: "Can you partition &quot;after&quot; install?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-30
I've installed Ubuntu Dapper 6.06 and chose the selection during install to use entire hdd instead of having the Live CD partition into the three partitions /home /swap /use rest of drive.

Can I have gparted make these three partitions from Live CD _without_ messing up my install? I have worked for weeks to get this ATI Radeon9200SE not to crash. It seems that it is finally working right. I would hate to mess it up. Then again, maybe it is just wating for me to turn my back. lol

BTW, can I save this entire setup the way I have it to a CD? I mean the entire Dapper program with my tweaks. If it is working, I will definitely want to save it to disk(s). I hope that I know enough to be asking the right kind of questions.
kh
Edit: If this is possible, be clear on how I can get gparted to place Dapper in the right partition. Thanks.

---

### Post by floke on 2007-03-30
Yes, you can repartition from the liveCd, or from a liveCD of gparted, or from this: [www.sysresccd.org](www.sysresccd.org)

Just shrink your single partition (entire HD) and then format and repartition the remaining space as you wish. Setting up a separate home directory is a good idea. A good guide can be found here. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You can also use partimage to make an ISO image of an entire partition (see Aysiu's page for thjis also)

You could also try this - although I haven't done it myself...

[http://ubuntuforums.org/showthread.php?t=390331](http://ubuntuforums.org/showthread.php?t=390331)

Hope this helps

---

### Post by kittyhawk63 on 2007-03-30
> **Steve.K said:**
> Yes, you can repartition from the liveCd, or from a liveCD of gparted, or from this: [www.sysresccd.org]("http://www.sysresccd.org")

Just shrink your single partition (entire HD) and then format and repartition the remaining space as you wish. Setting up a separate home directory is a good idea. A good guide can be found here. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You can also use partimage to make an ISO image of an entire partition (see Aysiu's page for thjis also)

You could also try this - although I haven't done it myself...

[http://ubuntuforums.org/showthread.php?t=390331](http://ubuntuforums.org/showthread.php?t=390331)

Hope this helps

Thanks again. This is really good stuff.

---

