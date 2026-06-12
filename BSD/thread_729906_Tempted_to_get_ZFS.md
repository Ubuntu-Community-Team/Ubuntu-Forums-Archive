---
title: "Tempted to get ZFS"
date: 2008-03-20
forum: BSD
---

### Post by dmitrijledkov on 2008-03-20
Well I really like ZFS concept. Forget partitions, yeah!!!!!!!

But it will never make it into linux kernel only into Fuse. (Can you install linux onto Fuse? or at least most of it except /boot?)

Therefore I seriously thinking to go FreeBSD or OpenSolaris or derivatives. Since they have native ZFS.

What is the biggest thing I'm going to miss from ubuntu? Hardware/software/community? Any big underlying rocks?

---

### Post by scottro on 2008-03-20
ZFS is VERY resource intensive.  The FreeBSD mailing lists still have lots of posts about problems with it, though most people seem to have it working well for them. 

Hardware support will probably be the biggest issue--for example, FreeBSD doesn't do well with flash 9, only flash 7.  Hrrm, wonder what happened to 8, but anyway...people do get it working in Wine though.  

Most software available for Linux should run on FreeBSD, even if sometimes, you have to use the Linux emulation layer.  There is PCBSD which is a GUI oriented spin on it, but in general, there's a lot more command line work. 

The support is there, but somewhat less newcomer friendly than these forums. That is, here, someone might post, my wireless isn't working, what do I do?  Someone will give them instructions as to what information we need to help them.  On a FreeBSD list, such a post might just be ignored, or at best, get check the handbook then post again. 

I haven't used OpenSolaris in over a year--FreeBSD would be less of an adjustment, judging from my admittedly dated experience.

So, the biggest things, I think, will be some hardware (though most can be gotten to work) and the fact that it's much more command line work.  

ZFS isn't native by default in FreeBSD by the way.  There are various articles and howtos about it though.

---

