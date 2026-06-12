---
title: "Total dual boot 'noob' install help please."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Swerve1000 on 2007-01-24
Hi,

I have been trying to intsall Ubuntu on my desktop so as to be a dual boot.

There is one hard drive onwhich I have just done a fresh install of XP. 40gb hard drive and in the windows installation I created 35gb for XP (NTFS) and 5gb for Ubuntu.

All I want to do is install Ubuntu on the 5gb partition, it is currently blank.

When installing off the live cd  it says :-

Prepare partition
dev/hda1       ntfs             34gb
unallocated    unallocated  6gb

I choose the unallocated partition, then I am presented with this next screen :-

Prepare mount points

/media/hda1    34gb   Partition1disc primary hda1

OK, I DO NOT want to use the 34gb windows partition, I want to use the 6gb blank partition.

I've read the tutorial but it does'nt help me at all.

I just want to install Ubuntu on the already partitioned 6gb blank partition.

Can anyone help me please????????????????

---

### Post by hyper_ch on 2007-01-24
Can you say what is written on the screen totally? I think you've missed telling half of the things :)

---

### Post by Swerve1000 on 2007-01-24
Thanks!!

Ok, I will have to rerun the install again to do that.

My question is if I select to install on:-

Prepare mount points

/media/hda1    34gb   Partition1disc primary hda1



Will it overwrite my XP installation? All I need to know is that.

I just want to install on the blank 6gb partition.

---

### Post by hyper_ch on 2007-01-24
I don't think so... but I'm not sure as this doesn't look familiar from the installs I've made... hence my request for the whole information :)

---

### Post by j19sch on 2007-01-24
The message:
"Prepare mount points
/media/hda1 34gb Partition1disc primary hda1"

does not ask where to install Ubuntu.
It asks if it should mount your Windows partition on /media/hda1 so you can access your personal data from within Ubuntu.

---

### Post by hyper_ch on 2007-01-24
That's all there? What options do you have on the previous screen?

---

### Post by Swerve1000 on 2007-01-24
Thanks guys, especially j19sch

That's all I needed to know.

I'll try again now, for the 7 th time.


:roll:

---

### Post by Sef on 2007-01-24
Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for dual booting from the alternate cd.

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing") for dual booting from the live cd.

---

