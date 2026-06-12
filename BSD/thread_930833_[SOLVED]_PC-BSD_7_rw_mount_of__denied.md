---
title: "[SOLVED] PC-BSD 7: r/w mount of / denied"
date: 2008-09-26
forum: BSD
---

### Post by Niniel on 2008-09-26
> r/w mount of / denied. filesystem is not clean - run fsck
Got this problem with my PC-BSD test machine. 

Another error messages was:
> /dev/ad0s1a.journal unexpected inconsistency
Then I get a console, where running fsck or fsck -y (also recommended by system) produces:
> /dev/ad0s1a.journal Cannot figure out file system partition
A total of 4 sectors are reported damaged - 38764416 - 19. Doesn't look like the system can do anything about it though.
Booting with option 5 of the boot menu - verbose logging - hangs with
> (cd0:ata1:0:0:0): error 6
(cd0:ata1:0:0:0): unretryable error
Booting with option 4 of the boot menu - singly user - hangs with
> Geom_journal: journal 3195325951: ad0s1a contains data
Geom_journal: journal 3195325951: ad0s1a contains journal
Geom_journal: journal ad0s1a clean
Geom_journal: Bio_flush not supported by ad0s1a
Trying to mount root from ufs: /dev/ad0s1a.journal
Warning: / was not properly dismounted
and then with an error message about a missing medium in the CD/RW.
I have no idea how I brought this upon myself.
Last thing I did was download the gnome2.2.22 pbi, although when I tried to install it, it didn't really do anything so I'm not sure that has anything to do with it. Still, the system may be angry with me that I even contemplated throwing out KDE (it's driving me nuts though so it'll have to go - if I even keep this OS around).
Or maybe the shutdown process hadn't finished yet when I cut the power. I had a blank screen when I did it but the computer was still on.

Anyway, if anybody has any ideas, I'd appreciate it.
And if not... well, then I'll just put something else on that box. :)

---

### Post by Niniel on 2008-09-28
Looks like nobody here has an idea, which is fine, I already re-installed anyway. But the second time around I am again having shutdown problems (in that it won't shut down properly) and I had a non-fatal "/ not dismounted properly" error, so now I'm convinced that this OS isn't quite ready for prime time yet.
Maybe once they are done with beta testing.

---

