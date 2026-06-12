---
title: "can dapper be installed for dual boot"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by sachincool on 2006-12-12
i have win xp installed on my computer
i have started installing ubuntu 6.06 dapper drake
i have come upto partitioning
its only showing me two options
1.copmpletely erase harddisk
2.manually edit partition

i selected manually edit partition
but in the next window its not showing partition table
its showing me only 1 partition ,the whole disk
what could b the problem

---

### Post by az on 2006-12-12
> **sachincool said:**
> i have started installing ubuntu 6.06 dapper drake
i have come upto partitioning
i selected manually edit partition
but in the next window its not showing partition table
what could b the problem

What happens when you select automatic partitioning?  Don't worry!  It won't do anything unless you tell it to.

It will ask you to pick a new size of the original windows partition.  If that's not the case, this is a bug or a corrupt partition table.

And yes, Dapper can do dual boot perfectly well.

---

### Post by sachincool on 2006-12-12
i have come upto partitioning
its only showing me two options
1.copmpletely erase harddisk
2.manually edit partition

i selected manually edit partition
but in the next window its not showing partition table
its showing me only 1 partition ,the whole disk
pls help

---

### Post by az on 2006-12-13
Perhaps try defragmenting your windows partition and then try again?

---

### Post by Sef on 2006-12-13
Have you set up the partitions before hand?  If not, then it would show only those two options.   There would be only one partition as Windows like to use the whole disk.

Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") to learn how to dual boot.

---

### Post by az on 2006-12-13
> **Sef said:**
> Have you set up the partitions before hand?  If not, then it would show only those two options.   There would be only one partition as Windows like to use the whole disk.


Well, no, actually.

Provided there is enough free space, the installer should be able to move around some data and free up some space at the end of the partition.  It should offer this option.

Sometimes, there are blocks at the end of an NTFS partition that parted or libntfs cannot safely move and it will not try to do it instead of taking the risk.  Often this is corrected by defragmenting in Windows.  This is why a lot of people suggest you defragment your hard drive before installing Ubuntu.

Most of the time, this is not necessary.

If defragmenting does not solve the problem, then that shortens the list of possibilities quite a bit.  Either there is a bug in the installer or there is a corrupt partition table.  Windows can work just fine with a broken partition table since it will just ignore any other partition than the first one if it sees this and can still boot.

---

### Post by anjin on 2006-12-19
> **azz said:**
> Sometimes, there are blocks at the end of an NTFS partition that parted or libntfs cannot safely move and it will not try to do it instead of taking the risk.  Often this is corrected by defragmenting in Windows.  This is why a lot of people suggest you defragment your hard drive before installing Ubuntu.

This may be what's causing me re-partitioning problems.

I'm running the latest GParted liveCD and keep getting an error when I try to resize the NTFS partition on my Win XP Pro machine.  I've run defrag, but there are two files it can't move (both email files, one from outlook, one from thunderbird).

Should I focus on the defrag issue first?
Is GParted an appropriate tool to resize an NTFS partition?
What does "5 cups of ubuntu and a vanilla latte" mean?

Thanks!

---

