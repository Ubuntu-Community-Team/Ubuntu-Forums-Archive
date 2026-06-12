---
title: "Does ubuntu GNOME have a &quot;scan disk&quot; feature?"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2005-12-21
I've installed ubuntu for the second time and seem to be having trouble with the partioning of my hd. During the set up it showed a little lightning bold next to my ext3 partition (#1).

I'm up and running now and don't want to reboot like I did last time because it didn't work.

Can I do something like a "scan disk" or the like to check my hd and it's partitions?

---

### Post by dcraven on 2005-12-21
Running "sudo fdisk -l" should show you what drives you have on the machine. "fsck" can run checks on those drives. Type fsck[TAB][TAB] to see the scripts for different filesystems.

"man fsck" or "man fdisk" for more info.

HTH,
~djc

---

### Post by futz on 2005-12-21
[QUOTE=stroopwafe]Can I do something like a "scan disk" or the like to check my hd and it's partitions?[/QUOTE]
Yes. Google for "linux disk check" and you'll get a page of articles and tutorials on how to do it. I've done it only once (not enough to memorize the commands), so I can't directly help you.

There are different commands you use, depending on the filesystem you use.

---

