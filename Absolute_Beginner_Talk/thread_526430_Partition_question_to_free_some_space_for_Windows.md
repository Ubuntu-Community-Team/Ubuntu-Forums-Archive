---
title: "Partition question to free some space for Windows"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-08-15
Hi,

I have a basic question about partition but it seems not easy to solve it:

I have partition as 

sda1: windows 0--20GB, 
sda2 (linux): 20---50GB and 
sda3 (linux-swap):50--52GB

I need 5GB free space for windows: I want to extend as :
sda1: 0--25GB
sda2: 25--50GB
sda3: 50-52

How do I do that? Gparted from liveCD allows decreasing size from right-hand side (20--45GB) not
25--50GB.

so partitions becomes like: windows/ linux / windows / swap

I dont want this? Is it possible to do resizing as: windows / extended windows / linux/ swap

If not, is it a problem to have partition as  windows/ linux / windows / swap?

thank you,
findik

---

### Post by overdrank on 2007-08-15
> **findik1 said:**
> Hi,

I have a basic question about partition but it seems not easy to solve it:

I have partition as 

sda1: windows 0--20GB, 
sda2 (linux): 20---50GB and 
sda3 (linux-swap):50--52GB

I need 5GB free space for windows: I want to extend as :
sda1: 0--25GB
sda2: 25--50GB
sda3: 50-52

How do I do that? Gparted from liveCD allows decreasing size from right-hand side (20--45GB) not
25--50GB.

so partitions becomes like: windows/ linux / windows / swap

I dont want this? Is it possible to do resizing as: windows / extended windows / linux/ swap

If not, is it a problem to have partition as  windows/ linux / windows / swap?

thank you,
findik

HI I believe it is set as default to make the partition a the front of the system and I don't know how to change that, but as your last statement of windows/ linux / windows / swap yes that will work I have my laptop setup that way with the last windows partition setup up with fat32 partition to be shared with windows and ubuntu. :guitar:

---

