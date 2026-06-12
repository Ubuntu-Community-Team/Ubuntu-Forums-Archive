---
title: "Installation Question: Space Allocation for Partitions"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by crystal on 2006-07-02
I have two 80 GB hard disk drives that I want to use for my Windows XP + Ubuntu dual boot, and would like to ask for comments on my intended space allocation. I have 1 GB of RAM. The Windows partition will be NTFS, the other partitions Ext3 (and swap as Linux swap, of course). I intend to use /home as the shared data partition as well, as per this [Partitioning Windows and Ubuntu](http://psychocats.net/ubuntu/partitioning.html) tutorial.

HDD #1: / (20%), /home (80%)

HDD #2: Windows (60%), /usr and swap (40%, 1 GB for swap)

From what I understand most of the programs will be in /usr, so giving it around 30 GB of space seems reasonable. However, is the 16 GB or so of space for the rest of the root directory sufficient? What I have read on the Web seems to place it as 3 times more than enough, but the information may be outdated.

I intend to have HDD #2 as master and the lone drive when I install Windows, then connect HDD #1 and set it as master before installing Ubuntu. Is this approach correct?

---

### Post by woedend on 2006-07-02
16 GB while taking out /usr is more than enough.  Looks good.
I've never been a fan of making that many separate partitions (with windows I used a /, a swap, a windows, and a fat32 shared)
But the way you have it lined out should be fine.
One question(and not criticism) - what is the reason you put /usr on its own partition?  I rarely see this done anymore

---

### Post by crystal on 2006-07-02
> what is the reason you put /usr on its own partition?
haha, maybe I should have asked about my other possible space allocation configuration:

HDD #1: Windows (60%), / (40%)
HDD #2: /home, swap (1 GB)

For this one I would set HDD #1 as master and have both hard disk drives connected right from the start. However, then I would ask: is 30 GB of space sufficient for the root directory with /usr? I hope to install all sorts of packages to try out, especially software libraries for programming.

---

### Post by woedend on 2006-07-02
I could not dream of getting my root directory so large.  I'm sure its possible, but with all of the programs I need, I am using ~3 gigabytes.  If I installed a lot of fluff of packages I still couldn't imagine hitting even 20 gigabytes.  I guess it's possible to reach 30, but I don't think you'll do it honestly.

---

### Post by crystal on 2006-07-02
> I could not dream of getting my root directory so large. I'm sure its possible, but with all of the programs I need, I am using ~3 gigabytes. If I installed a lot of fluff of packages I still couldn't imagine hitting even 20 gigabytes. I guess it's possible to reach 30, but I don't think you'll do it honestly.
Oh dear, I must be too anxious about space limitations then :D

> but isnt your root partition going to be 40 gb in that configuration?
No, it will be around 50 GB for Windows and 30 GB for the root partition (60%-40%, not 50%-50%).

Now that I have a clearer idea of how much to allocate, I will choose the latter. Thanks for your help :)

---

### Post by woedend on 2006-07-02
lol...i edited my post I kept thinking they were 100 gb hard drives...absolutely right.
But I think the second setup is absolutely perfect for your needs.  Good luck!

---

### Post by crystal on 2006-07-03
Looks like I wasnt so lucky though :(

The installer kept on choking at the partitioning of my SATA hard disk drives. That problem went away when I used the alternate CD for the install, but it turns out that one of my hard disks is faulty. Everything went well right until the point when I tried to login, then the system just stalled. After a reboot, the startup stalled at 'Checking all filesystems'. Reinstalls did nothing to solve it, until I finally decided to unplug the drive that the filesystem check complained about.

Oh well, I'll just have to make use of my warranty tomorrow.

---

