---
title: "Partition Confusion"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-04-09
Can someone help me make sense of this please?

I have 2 hard drives, an 80 gig Western (hda) and a 40 gig Maxtor (hdb).

GParted shows:

hda1 - ntfs (Windows XP) - (61Gb)
hda2 - extended (15Gb)
hda5 - ext2 (Ubuntu home) (15Gb)

hdb1 - ext3 (Ubuntu) (36.5Gb)
hdb2 - extended (1.5Gb)
hdb5 - linux-swap (1.5Gb)

However, "Disks Manager" shows:

hda1 - ntfs (Windows XP)
hda5 - ext2 (Ubuntu home)


hdb1 - ext3 (Ubuntu)
hdb5 - linux-swap

So... what are hda2 and hdb2 and why are they shown in GParted but not in Disks Manager?

---

### Post by ubernoob on 2006-04-09
a disk can only have 4 partitions fram back in the old days. The solution is extended/logical partitions which can contain alot of them. (Not sure if there is a limit). So hda2 is an logical partition which contains hda5. To mount swap or ubuntu, you should use nr 5. If you delete hda2 you also delete hda5 and all other partitions that is a part of the extention.

Not sure if that was understandable :)

---

### Post by _simon_ on 2006-04-09
Thanks a lot it all makes sense now! :)

---

