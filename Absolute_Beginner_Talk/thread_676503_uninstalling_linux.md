---
title: "uninstalling linux"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by mowerman on 2008-01-23
my husband needs to uninstall linux from his laptop which also has xp professional installed. In searching for answers I came across this forum, but while registering, I lost the thread!

We have some problems in that the laptop came loaded with xp Pro so we don't have the discs, neither do we have a boot disc of any sort (floppy or cd).

I have found info as to deleting the liinux partitions but how do I  then make those partitions  available to the xp?

My apologies for it not being Ubuntu but this forum seems to have the best info on deleting linux

---

### Post by Borbus on 2008-01-23
I think you can overwrite grub by using windows recovery console and using fixmbr. You should look that up, though because I'm not sure.

When you have grub removed you can just delete the linux partitions with windows disk manager. Then you use that to make new partitions in the unallocated space (or you can extend your existing ones into the space).

You don't even have to remove grub, though. You can just reconfigure it to boot windows immediately. But then you would need to keep at least a /boot partition. If you don't mount /boot separately then I don't think you can do this, though.

---

### Post by jaytek13 on 2008-01-23
There is a disk administrator tool in XP that allows you to format partitions. All that would be required is you use this tool to delete the linux partitions, and then reformat them as ntfs, which will make the hard drive space available in windows. As far as I'm aware there is no way to "integrate" the extra space so that it's all on one partition, but this may be possible. Either way, having 2 partitions simply act as if they were separate hard drives. From xp, after you delete linux and format ntfs, you will be able to access and save files and programs and music and movies or whatever you want to the second partition... it would just be the "E:/" drive instead of the "C:/" drive.

---

### Post by Paul820 on 2008-01-23
Do you have a linux live cd? If so you can try this [http://www.arsgeek.com/?p=3340]("http://www.arsgeek.com/?p=3340")

---

