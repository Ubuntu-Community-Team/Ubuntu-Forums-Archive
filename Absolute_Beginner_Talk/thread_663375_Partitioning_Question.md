---
title: "Partitioning Question"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Loafers on 2008-01-10
I finally installed Ubuntu on my laptop along with Windows and it's pretty awesome.  

However I I accidentally gave my Ubuntu partition too much space.  Is there some way to transfer empty hard disk space to my Windows partition?

I tried using fdisk, but I'm totally clueless...

---

### Post by Xavieran on 2008-01-10
You can boot into the LiveCD and select System>Administration>Partition Editor (or GParted)

You have to use a LiveCD because it needs to unmount your partitions to edit them...

The Partition Editor is pretty user-friendly ,so you should be fine...:)

---

### Post by Paqman on 2008-01-10
It's always a good idea to back up your data before messing about with partitions, too.

---

### Post by hyper_ch on 2008-01-10
> **Paqman said:**
> It's always a good idea to back up your data before messing about with partitions, too.

I'd like to add that it's always a good ieade to make regurarly backups ;)

---

### Post by Paqman on 2008-01-10
> **hyper_ch said:**
> I'd like to add that it's always a good ieade to make regurarly backups ;)

Sbackup is your friend ;)

---

### Post by hyper_ch on 2008-01-10
rsync and the concepts hardlinks as well as cron all combined to a shell script work marvellously

--> every 6h an incremental snapshot-style backup dating back for 90 days.

---

### Post by Xavieran on 2008-01-10
Wow...every six hours? You must have a lot of disc space!

My backup script does it for every half week...

P.S...You made it past 3000 beans this week ;)

---

### Post by hyper_ch on 2008-01-10
using hardlinks doesn't use that much space ;)

Thx for the beans ;) didn't notice ;)

---

