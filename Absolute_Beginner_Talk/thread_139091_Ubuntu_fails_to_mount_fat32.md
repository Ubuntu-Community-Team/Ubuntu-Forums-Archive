---
title: "Ubuntu fails to mount fat32"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-03
I had a ntfs partition (hda5) for my documents in windows XP. To be able to fully share files in this partition by both Win and Ubuntu, I tried to change it to fat32.

When I started Ubuntu, it automatically mounted the other ntfs partitions while booting, but failed to do so for the new fat32. How do I ensure hda5 (fat32) is also mounted during boot?

I went to fstab and noticed that the file type for hda5 was still ntfs, so I changed it to fat32. That has made no difference.

Anyway, even when I mount hda5 manually, I see a new problem when I try to open files (htm, doc excpt pdf) in it. Previously when it was still ntfs, the files would open at once. But with fat32, it says "Do you want to run file...file is an executable text file". If I choose to display, then it opens. This requires unnecessary effort and does not make sense to me.

---

### Post by akiro.yamamoto on 2006-03-03
The fstab entry should be changed to something like:
/dev/hda5       /media/data     vfat    user,umask=000        0       0
Hope this helps.
Check my sig for ubuntu set-up.
BTW: Welcome to Ubuntu Linux ;)

PS:
Fat32 has no support for Permissions so the default action is to give all permission globally for all the file
on that partition.
Typically I use ext3 partitions and install the ext3 driver in windows if I want to exchange info between
the two OS. Ext3 has better file support, error recovery support and permission support.

You might try the noexec option to get around that.
/dev/hda5       /media/data     vfat    user,noexec,umask=000        0       0
but I cant remember the correct umask number.

---

### Post by AtinLango on 2006-03-03
A million thanx. It worked.

Only my second problem of opening files remains.

---

