---
title: "How dod I Dual boot two Linux Distros?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by The Iron Curtain on 2007-01-04
Hi,

I'm building a new computer and I just wanted to know about dual-booting two Linux Distros. I'm fairly new to Linux, but I've picked up quite abit in the last few months. 
Here are my questions:

1. Can I share a single Home partition between two (or more) Linux Distros?
2. Can I share a single Swap partition between two (or more) Linux Distros?
3. Do I need to know anything else before I embark upon this journey?

So far I know that Ubuntu (and other distros) use the GRUB Bootloader which handles dual and multi-booting, and that Ubuntu (and other distros) use the ext3 file format.


Thank you all!

---

### Post by Lord Illidan on 2007-01-04
You can share home partitions, but beware, as there can be issues with user ids, etc. I'd rather use different partitions for /home, especially when I have a large harddrive.

However, the swap partition can be shared with no problems whatsoever.

---

### Post by The Iron Curtain on 2007-01-04
Thank you! If I make a seperate partition for /opt (for my programs) in Ubuntu, can I share that with the other distro?

---

### Post by mykalreborn on 2007-01-04
it's recommended not to share home partitions as there can be issues with user settings and such. you can choose to make a different partition and mount it in /mnt/data or something like that and use it as your second /home. i would have both /home partitions on the root partitions of their distros and make a bigger fat32 partition - in case you want to install windows :p - and use it as a place to save your files, but make sure no program files get in the way.
and all the modern distros have grub installed form what i know, and they'll detect the other distro without any hassle.

---

### Post by mykalreborn on 2007-01-04
> **The Iron Curtain said:**
> Thank you! If I make a seperate partition for /opt (for my programs) in Ubuntu, can I share that with the other distro?

i dunno if that's a good thing. the best would be to leave the two distros program files sepparate of each other.

---

