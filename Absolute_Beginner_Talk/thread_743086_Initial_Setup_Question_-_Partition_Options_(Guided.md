---
title: "Initial Setup Question - Partition Options (Guided vs Manual)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-04-02
Hi,

I am setting up Ubuntu on another one of my machines.  This has an 80 gig drive.  I have it set for 30gigs XP, 10 gigs Fat32), & the rest I would like for Ubuntu.

I have noticed in the past, that my partitions for my previous ubuntu installs have everything as one large directory.

I was under the impression if I wanted to reinstall ubuntu (delete the old partition using Gparted) with a fresh install that there was a way to keep your user files & settings in another partition.  

Does Ubuntu not do this by default?  I assume if I have one large ext3 partition that Ubuntu creates & I want to do a reinstall or install another version of Linux/Ubuntu , that I would have to back all my data up as I only have one partition.  

I ask because very soon I will be trying Hardy (once its released).  Should I have another partition?  

I am very confused as I hear people talking about having different versions of linux running on multiple partitions.

Thanks
Rich

---

### Post by jken146 on 2008-04-02
If you want another partition for your users' files, you need to use the manual partitioning option in the installer.  Create 3 partitions in total:

[LIST]
[*]10 GB ext3, mounted on /
[*]RAM x 1.5 or 1 GB (whichever is smaller) for swap, at the end of the disk
[*]The rest of the space for /home, ext3
[/LIST]

---

### Post by Calash on 2008-04-02
By default the guided partitioning will take your whole drive and make 2 partitions, the swap and the root (/).  This will also delete your Windows XP install, so you will want to use the Manual option.

What you are talking about is having the /home directory on a separate partition.  It does have the benefit of preserving your data should there be a OS issue.  Upgrading to Hardy will not delete your data if you use the update manager, but it is still not a bad idea to set it up.

I found this guide...a bit hard to follow but it does have all the info on making a separate /home

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by RichTJ99 on 2008-04-02
> **jken146 said:**
> If you want another partition for your users' files, you need to use the manual partitioning option in the installer.  Create 3 partitions in total:

[LIST]
[*]10 GB ext3, mounted on /
[*]RAM x 1.5 or 1 GB (whichever is smaller) for swap, at the end of the disk
[*]The rest of the space for /home, ext3
[/LIST]

Is there partition software that will make that for me.  Years ago when I was playing with redhat, I think their partitioner did that for me (maybe not).  

How do I set it up so my /home folder has all my settings & files?  What should be in /home?

---

### Post by RichTJ99 on 2008-04-02
> **Calash said:**
> By default the guided partitioning will take your whole drive and make 2 partitions, the swap and the root (/).  This will also delete your Windows XP install, so you will want to use the Manual option.

What you are talking about is having the /home directory on a separate partition.  It does have the benefit of preserving your data should there be a OS issue.  Upgrading to Hardy will not delete your data if you use the update manager, but it is still not a bad idea to set it up.

I found this guide...a bit hard to follow but it does have all the info on making a separate /home

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)


Hi,

 I keep hearing that a fresh install is much better than an upgrade.  I know in the windows world that is by far the case.  

Thanks,
Rich

---

