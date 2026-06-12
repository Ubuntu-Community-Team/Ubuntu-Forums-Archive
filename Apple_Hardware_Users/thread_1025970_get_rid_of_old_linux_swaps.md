---
title: "get rid of old linux swaps"
date: 2008-12-30
forum: Apple Hardware Users
---

### Post by maclin on 2008-12-30
i tried get ting ubuntu to work on my mac about 6 times, no worky now i have erased the proportions but i cannot get  rid of the linux swap files

---

### Post by mkvnmtr on 2008-12-30
Boot the live disk and go to the partition editor. This is GParted. You should see all yourn partitions. All the swap partitions will be there. They will be locked. Look for swap off under device or view or one of those others, I always forget and have to look. Cilck swap off and you can delete nthe extra swap partitions. If you have more than one listed boot partition think a long time before you try to delete them.

---

### Post by stream303 on 2008-12-31
If you want to dedicate the whole disk to Ubuntu, the easiest method is to use guided-partitioning and let it "use the whole disk".  That way the two special apple partitions that need to be present will be automatically created, along with the usual root / and swap.  Apple ppc needs at a minimum 4 partitions for hfs, boot, root and swap.  ( I guess one could leave out swap if they really wanted).

A neat trick that used to work was to do the above, and then if you wanted custom partitioning (leaving the hfs and boot partition untouched) was to use the "go back" method to erase/resize your root and swap (and others if you wanted /var /tmp /home) etc before taking that final step of writing the partitions to disk.

I don't know what Ubuntu did, but the "go back" method no longer works in Intrepid for custom partitioning making things just that bit a little harder.  Thats another point in Debian's favor - they didn't touch the partitioner which makes it easier for us ppc'ers to do custom partitions via the "go back" method.

At any rate, "use the whole disk" certainly works, although you better have backups if anything is important to you.

---

### Post by cyberdork33 on 2008-12-31
> **stream303 said:**
> If you want to dedicate the whole disk to Ubuntu, the easiest method is to use guided-partitioning and let it "use the whole disk".  That way the two special apple partitions that need to be present will be automatically created, along with the usual root / and swap.  Apple ppc needs at a minimum 4 partitions for hfs, boot, root and swap.  ( I guess one could leave out swap if they really wanted).

That being said, there is an important distinction to be made... Are you using a PowerPC mac or an Intel one?

---

