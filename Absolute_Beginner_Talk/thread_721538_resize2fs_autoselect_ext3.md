---
title: "resize2fs autoselect ext3?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by PCFascist on 2008-03-11
I am using resize2fs to 'grow' a partition, because it is apart of an LVM QTParted doesn't know what it is, so I have to use the command line tool.
My question is how do I pass to resize2fs that it is ext3 and not ext2 (Yes, I've read the man page)? I now have the volume group mounted and mount tells me that this is mounted as ext3, but can I trust mount?


Thanks!

---

### Post by RealPSL on 2008-03-14
You made me go back and read the man pages myself and I might be missing something but resize2fs which works on both ext2/3 file systems does not require a parameter to tell it if the file system is ext2/3. Where are you seeing this parameter.

What I did was extend the logical volume. Unmounted the file system (it says it can be done online but this is my PC I am not providing 24/7 service to anyone) and then used resize2fs to perform the extension. Mounted it back up and the new file system size was there. Yes my file systems are all ext3.

---

