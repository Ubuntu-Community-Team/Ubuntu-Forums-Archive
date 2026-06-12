---
title: "Help -Update manager keeps trying to download kernel even though deselected"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-06-06
I tend not to update the kernel unless something really significant to me is in it as I do not like to have to recompile stuff (I'm more of a "I just want it to work" guy).  I normally let update manager download whatever it wants except I deselect the kernel patches.

For some reason now update manager thinks it has kernel updates to install even though every file is deselected.  In other words, right now update manager shows 8 files/packages/updates to download.  6 are kernel, 2 are prog updates, YET update manager says there are 12 updates.  The 4 extra files not seen on the list (totaling 46.6 meg) are kernel updates and there is no way I can tell it not to download them.  I have been updating by watching the updates download and cancel as soon as a kernel patch starts to download.

How can I make update manager stop trying to download these phantom files?  There's got to be a way.

---

### Post by meng on 2007-06-06
Go to System > Administration > Synaptic Package Manager
select the kernel packages you want to fix to their current version
and then select the option "Lock Version"

---

### Post by Atomic Dog on 2007-06-06
Hey meng.  You da man.  I owe you a cold one.  Just come to Phx to claim it ;)

---

