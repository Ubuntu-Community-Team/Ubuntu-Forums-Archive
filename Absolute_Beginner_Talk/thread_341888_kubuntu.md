---
title: "kubuntu"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Wonslung on 2007-01-19
hello, i'm new to ubuntu and linux.  After a rocky start for the past couple days i thought i was finally getting somewhere so i decided to give kde a try and downloaded the packages

i like it a whole lot better but i'm still very far from being able to solve isses i create

my compter is set up like this: 2 hard drives

first hard drive has grub, then a 10 gb primary partition with windows xp, extended partition with a 10 gb logical partition for program files and games

second hard drive has 10 gb primary partition with kubuntu, extended partion containing 2 25 gb  fat32 partitions ( f and g in windows, unmounted in linux) followed by the linux swap partiton

my problem is this, i've been trying various ways to get the fat32 partitions mounted because this is where i save multimedia files and torrent downloads...in doing this "screwing around" i opened 
System Settings Disks and File systems under the advanced tab
clicked on Administrator mode and tried to create mount points that way..now i have icons on my desktop that i cannot delete and the drives STILL aren't mounted ..please help

---

### Post by tommytom on 2007-01-19
Could you post your fstab file please? use ```
sudo gedit /etc/fstab
``` to view it and we can have a look a whats going on ;)

Ps - use a terminal to enter the code.

---

