---
title: "Reformatting External USB Drive from NTFS to ext3"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by lifeinoleg on 2008-01-13
Hi,

Wondering how I would reformat my external USB Drive that I had when I was still using WIndows to be able to read/write (it already reads, mainly write). Everything from it is backed up somewhere else, so I'm not worried about losing the data.

In Windows I just gave it the 'ole format d:, but I don't know how to do the equivalent in Ubuntu :(

I got GParted, but I can't seem to make it do anything with the external drive.

Thanks for the help.

---

### Post by edm1 on 2008-01-13
What isnt working when you try to format it using gparted? Remember you will have to unmount it first. You can do that either in gparted or by right clicking on the drives icon on the desktop.

---

### Post by logos34 on 2008-01-13
like edm1 says, you have to unmount it first.  (It might keep trying to automount it, which can cause problems, so turn that feature off -->system>prefs>removable drives & media>storage tab>uncheck all)

Try this to add write access:

[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by lifeinoleg on 2008-01-13
edm1, no I did not unmount it first. Didn't realize I had to do that. That's probably why it wasn't working. --- There, just unmounted and everything looks in order. (I didn't even think of unmounting it)...

logos34, thanks for the link. I think I'll try that first before reformatting.


Thank both you for the prompt help. Much appreciated.

---

