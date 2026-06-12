---
title: "Hiding HFS+ Partitions from Ubuntu (and EXT from OSX)"
date: 2011-12-15
forum: Apple Hardware Users
---

### Post by RMOP on 2011-12-15
I appreciate that most folks are concerned with gaining R/W access to their HFS+ partitions from within Ubuntu. While that's been discussed a lot here, I've not found a discussion about how to HIDE such partitions from Ubuntu. There are some HFS+ partitions that I don't want Ubuntu to "see," and likewise, I don't want OSX to be aware of certain EXT partitions.

Which fstab entries for Ubuntu and OSX, respectively, would be appropriate for hiding "other OS" partitions from non-privileged users? Meaning, not having them show up in "Places" in Ubuntu, etc.

---

### Post by jmate24 on 2011-12-16
for ubuntu you would go into synaptic and uninstall these packages so that ubuntu cannot see the osx hfs partitions:

hfsplus
hfsprogs
hfsutils
hfsutils-tcltk
libhfsp0

but i am not sure how to prevent mac from seeing ext2/3/4 or btrfs but if you were to check the apple support website i think you may find answers there.

BTW: I really don't own a mac myself but I own a mac mouse and keyboard and i love them.

---

### Post by RMOP on 2011-12-16
Jmate24 - thanks for the reply. Your solution would work, it seems, to prevent ANY HFS+ access whatsoever from Ubuntu. I'm actually hoping for a more nuanced approach, which will let me exclude specific partitions while retaining access to others for which common access is desirable. That's pretty much what I've done with a shared NTFS partition on which my shared FireFox profile is stored.

And, while I'm on a ramble, I really need to exclude non-data NTFS partitions from OSX as well...I've managed to do that from Ubuntu.

I'm fairly certain that all of this can be handled by the proper fstab entries. I'm even more certain I'll (again) render my Ubuntu and/or OSX system at least temporarily unbootable before I stumble upon the right configuration by trial and error.

So, I want to retain the ability to read HFS+ from Ubuntu and EXT from OSX, but also to be able to restrict that ability to specified partitions.

Thanks again for your input. I'll hope someone else will take an interest in this topic and point in the right direction.

---

