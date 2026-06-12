---
title: "Installing Ubuntu."
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by Itachi on 2005-10-20
Hello, everyone. :)

I have the iso for Ubuntu, and I burned it onto a disc, and started to install. I got stuck with the partitions stuff, and I have no idea what to do. Could someone please help me?

---

### Post by LHZ on 2005-10-20
What do you want to do?

If the computer you're installing Ubuntu on doesn't have an operating system on it yet (like windows), you'll just need to make one or two partitions. Ideally, you'll have a big normal partition, and a partition that's about twice the size of your ram to store your swap file.

If you already have windows (or something else) installed and would like to keep using it, it's important that you DO NOT repartition everythoing from the beginning, as this would lead to the loss of all your data. In this case, you'll have to tell the installer to leave windows alone, and install to a different partition. It's very well possible that this new partition doesn't exist yet. In that case, you'll need a partitioning tool (such as Partition Magic, altough there are free alternatives available) to split the hard drive into multiple partitions. Windows and ubuntu don't like being in the same space.

Could you give us some more information on what's on your computer, what the size and partitions of your harddisk are, and what you would like to use the computer for after the Ubuntu installation? If any of the terms I used confuse you, just mention it.

---

