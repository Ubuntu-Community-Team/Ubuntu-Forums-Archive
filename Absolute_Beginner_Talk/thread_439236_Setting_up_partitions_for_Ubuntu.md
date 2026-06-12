---
title: "Setting up partitions for Ubuntu"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by BoysBoysBoys on 2007-05-10
Hello,

When I installed windows xp I made sure I made a seperate partition of 40GB for ubuntu. When I went to install ubuntu it wanted to split my windows partition naturally. I tryed the custom approach but it was too complicated for me. My question is how many partitions does ubuntu use default? does it need a ext2 partition and a ext3? I think I need a swap partition as well? how would you divide the partitions among 40GB?

---

### Post by kragen on 2007-05-10
At it's simplest all you need is a root partition ("/") and a swap partition. You could make it more complicated if you wanted to, but its debatable whether or not it would have any real advantages.

I would probably create a 500 MB to 1GB swap partition depending on how much memory you have, and then use the rest to create one ext3 partition for everything else (the root "/" partition). (ext3 is basically an "updated" version of ext2).

---

### Post by mikewhatever on 2007-05-10
You'll need two partitions (root, swap) for the basic set up. Root should be formatted as ext3 and swap is not formatted.

---

### Post by BoysBoysBoys on 2007-05-10
When you set up ubuntu normally does it just make one ext3 partition and one swap partition? Also I have 2GB of ram, so how much swap would you suggest?

---

### Post by annda on 2007-05-10
> **BoysBoysBoys said:**
> When you set up ubuntu normally does it just make one ext3 partition and one swap partition? Also I have 2GB of ram, so how much swap would you suggest?

yes on the first question - just don't wipe the entire disk! and defragment it before resizing.

you have a lot of RAM, so 1 GB swap should be enough (it is usually 2xRAM, but that would be wasted disk space).

---

### Post by ronmarley1 on 2007-05-10
Additionally, it's not a bad idea to create a separate partition for /home.  Then, if you need to reload the OS, you can save your data.

---

