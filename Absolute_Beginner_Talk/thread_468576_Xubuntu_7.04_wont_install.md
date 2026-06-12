---
title: "Xubuntu 7.04 wont install"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by DreamcastJack on 2007-06-09
i try to take over the whole hard drive for xubuntu..cause I wanted light weight and fast.  Ubuntu installed..no problems.. but I get this error w/ Xubuntu

"The ext3 file creation in partition #1 of IDE1 master (hda) failed"

what do I do?

---

### Post by ugm6hr on 2007-06-09
Are you using the LiveCD or AlternateCD?  And which Xubuntu version?

If the LiveCD - try removing all pre-existing partitions on the HD before trying to install.  Many ways to do this:
From LiveCD - in Terminal: *cfdisk* - then just delete all partitions.

If not - try ActiveKillDisk (search for it on google) or GParted LiveCD (which is a useful CD to have anyway).

Then try again.  

I believe this problem is caused by the fact that Ubuntu won't allow you to write over itself.  So you have to manually delete it, then reinstall.

PS: I prefer Xubuntu to Ubuntu.

---

