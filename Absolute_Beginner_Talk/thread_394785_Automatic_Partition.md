---
title: "Automatic Partition"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-03-27
I might be installing Ubuntu 6.05 LTS and just wanted to (as im a noob to partitioning) if I choose
for Ubuntu to automatically partition my drive which is 55GB with 36.6 GB Free (may be more soon) how much will it make my Ubuntu as I have a portable drive which is FAT32 for storage and want to dual boot with Windows XP which is installed.

So how big will my ubuntu partition be?
And can it be resized at a later date?

:KS

---

### Post by zvacet on 2007-03-27
It will be exact same size as free space.You can resize it later.Better way is to partition it right now,and it is not same sort of scietific project.if you want to accept my sugestion do it this way:

1. root =no more then 10GB   mountpoint /
2. home = rest of free space exept     (mountpoint home)
3.swap =1GB
But you can do it as you choose and resize it later with Gparted Live CD.

---

### Post by SamTyson92 on 2007-03-27
Do I need the home one?

---

### Post by wscheer on 2007-03-27
Sam,
I did something similar to your setup this weekend.
I had a windows xp home laptop that I am dual booting with Ubuntu now.

I did some google action on partitioning ,because I am a partitioning noob too, and I found a good guide for partitioning. [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

read that guide a few times. trust me it will make sense the second time. :) 

I did a clean install of windows xp and that might not be an option for you.
My hd was a 60 GB so I partitioned it like this:

20.0 GB for Windows XP Home Edition
5.0 GB for /  (root) for Ubuntu Dapper
20.0 GB for /home for Ubuntu Dapper
11.0 GB FAT32 data partition       (shared files Windows/Ubuntu)
1.0 GB Swap Area                        (memory swap)

This is kind of how it worked out
primary (windows)
primary (ubuntu)
-extended {
-- /home
-- /windows
-- /linux swap
}

You can probably give more space to your "/home" since you'll be using a portable drive as your shared space.

I installed ubuntu and I have pretty good amount of programs and I have only used about half of the 5 GB's

Hope this helps a little bit.

---

