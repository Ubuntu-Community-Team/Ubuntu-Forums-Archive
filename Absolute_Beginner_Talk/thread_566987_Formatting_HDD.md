---
title: "Formatting HDD"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-10-04
I just bought another desktop PC,  installed Windoze (need it for 2 critical reasons), on half the drive's capacity (formatted NTFS), but leaving the balance of the drive free.

I've previously installed Feisty Fawn OK, using the partitioning option in the install to make /, home and swap.

Now, can I do the same again, AS WELL AS formatting an amount of free space to use as an additional Windoze partition, FAT32?

I can't see why I can't do this, and I suppose I'd partition the MS logical drive at the start of the free space, leaving it as one drive number behind the C: drive. Then I'd do the Ubuntu partitioning. Does this make sense? And if so, is there a facility in the Ubuntu partitioning to give the MS partition a name I require?

Any help appreciated - I could just go ahead and do it - but I'd rather know what was possible before I proceed. Thanks.

---

### Post by forestpixie on 2007-10-04
I would do that with a [gparted]("http://gparted.sourceforge.net/download.php") live cd myself - in fact I did, then when it comes to installing Ubuntu just pick up the partitions already made

As far as naming the fat32 partition I would name it in MS before I installed Ubuntu

---

### Post by hyper_ch on 2007-10-04
Well, you can only have 4 primary partitions.... so far you very likely have all 4 already:

- ntfs
- swap
- home
- root

What would be the best now is to delete the swap one, then you are using only 3 primary partitions...

Then you need to resize the other partitions so that the unpartitioned (ex-swap) space becomes as large as you need.

Then create an extended partition and within that extended one, you can create a logical SWAP partition and a logical Fat32 partition...

But why do you want a Fat32 partition anyway? Install the ext2/3 drivers and you can read/write to your linux partitions.

---

### Post by corowakid on 2007-10-04
> **corowakid said:**
> I just bought another desktop PC,  installed Windoze (need it for 2 critical reasons), on half the drive's capacity (formatted NTFS), but leaving the balance of the drive free.

I've previously installed Feisty Fawn OK, using the partitioning option in the install to make /, home and swap.

Now, can I do the same again, AS WELL AS formatting an amount of free space to use as an additional Windoze partition, FAT32?

I can't see why I can't do this, and I suppose I'd partition the MS logical drive at the start of the free space, leaving it as one drive number behind the C: drive. Then I'd do the Ubuntu partitioning. Does this make sense? And if so, is there a facility in the Ubuntu partitioning to give the MS partition a name I require?

Any help appreciated - I could just go ahead and do it - but I'd rather know what was possible before I proceed. Thanks.

Used GParted live CD and it did the trick.

---

