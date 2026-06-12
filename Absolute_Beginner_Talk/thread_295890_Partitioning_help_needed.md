---
title: "Partitioning help needed"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Tobias Phoenix on 2006-11-08
I have a 160GB hard drive with Windows XP already installed on it. I have downloaded the latest version of Ubuntu and would like to install it on the same drive, but am not quite sure how to do this. I want to be able to share files between both Ubuntu and XP (read and write) but mostly I'd use Ubuntu. (I'm keeping XP just for those little things that Ubuntu can't do as well). If anyone can tell me the best way to set up the partition/s (and how to do this) it would be greatly appreciated. (A friend suggested leaving XP with a 30GB partition, and the rest being shared file space and Ubuntu, if that helps)

---

### Post by ThrobbingBrain66 on 2006-11-08
30GB - windows
15GB - ubuntu
114GB - vfat (shared space)
512MB-1GB - swap space

this is just a simple setup using all primary partitions (only 4 are allowed), but should suit your purposes.  you can make these partitions by booting to the live cd and running gparted before doing the install. gparted can be found in system>administration>gparted

then before you actually install, you will be given the oportunity to assign these partitions to the proper place.

---

### Post by Tobias Phoenix on 2006-11-08
Thanks for that. I've never really partitioned anything before, so...But I'll give that a shot now.

---

### Post by Sef on 2006-11-08
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/"), if you're using the alternate cd.

Read [Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing"), if you're using the Live CD.

---

### Post by ThrobbingBrain66 on 2006-11-08
> **Tobias Phoenix said:**
> Thanks for that. I've never really partitioned anything before, so...But I'll give that a shot now.

and certainly if you have more questions dont be afraid to ask.

---

### Post by Tobias Phoenix on 2006-11-08
> Read Installing Ubuntu, if you're using the Live CD.

I've been looking for that site for a few days now, thanks for the link.

> 114GB - vfat (shared space)

What do you mean by vfat? It's not a format option, do I use fat32?

---

### Post by BlocknBleed on 2006-11-08
FAT32 should work. I have 2 hard drives on my comp so on the linux drive I put a fat32 partition so I can read and write to it from both OS's and transfer files and stuff. It seems to work great so far. 
Good luck.

---

### Post by ThrobbingBrain66 on 2006-11-09
> **Tobias Phoenix said:**
> I've been looking for that site for a few days now, thanks for the link.



What do you mean by vfat? It's not a format option, do I use fat32?

vfat = fat32

---

