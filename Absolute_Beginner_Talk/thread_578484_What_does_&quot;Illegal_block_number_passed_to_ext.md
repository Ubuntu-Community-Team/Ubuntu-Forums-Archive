---
title: "What does &quot;Illegal block number passed to ext2fs_test_block_bitmap&quot; mean"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-17
I ran badblocks and got a list. I used debugfs to find if the blocks were in use with testb blocknumber

And it reports back this weird stuff "Illegal block number passed to ext2fs_test_block_bitmap" and says the block is not in use though.

Anybody know what this message means.

---

### Post by LanDan on 2007-10-22
no clue,

according to google it is some rare bug in the file system, no idea what causes it and if it could be harmful.
wich partition is it?

---

### Post by philinux on 2007-10-22
It's my large home partition.

I'm getting no errors in message.log and smartctl reports passed. But if I run fsck i.e. force it it finds illegal block numbers which can be fixed by overwrite but then I get the dreaded seekread errors pop up in message.log

Hence trying to get rid of bad blocks.

---

### Post by LanDan on 2007-10-22
if i were you i would play it save and backup my home and re-format the whole partition
if you have that option offcourse and then do another check, might give you a clue if its hard drive failure or file system problem

---

### Post by philinux on 2007-10-22
Already did that a month ago after backing up my home folder. Did the guided install then after decided to make a home partition.

Been running like that since and just disabled fsck for /home. About 2 weeks ago I did a sudo touch forcefsck to see what would happen. Same old story fsck died with errors status 4 "error reading block etc"

Upgrade last week and running fine - might just leave it.

---

### Post by LanDan on 2007-10-22
as long as you promise not to keep your scientific papers on how to solve the ebola virus on there you can take that chance, if it happens even after you re-formatted it could verry well be your hard drive i think

---

### Post by philinux on 2007-10-22
Thats my conclusion but because its a big partition the bad bit is not getting used so no drive errors during normal use.

When home was a folder within the main partition and fsck ran it hit the bad bit I think. When fsck runs on /dev/hda1 it finds no probs now as that is just root

---

