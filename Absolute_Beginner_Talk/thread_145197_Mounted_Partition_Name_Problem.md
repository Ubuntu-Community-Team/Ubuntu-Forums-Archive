---
title: "Mounted Partition Name Problem"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2006-03-15
Hey,

I have a problem. i jsut got a new 100gig laptop hard drive and one of the partitions in a 20gig fat32 partition at hda6.. and thats exactally how it shows up as the link on my desktop... i changed the mount point in my fstab file and rebooted... what am i doing wrong? i want it to be called something like Internal or something... can anyone help me ^_^ thanks.

~Lance

---

### Post by patrick.ubuntu on 2006-03-15
Hi Lance,
I might not be understanding the question, but here's what I think the answer is-
the name that linux will give a partition is what the mount point is.  So, I'm mounting /dev/sda2 at /media/xp, which linux mounts and puts a link on my desktop as "xp".  What are you mounting the partition as in your fstab?
Hope this helped,
pt

p.s. I'm still  working on the mouse issue that you had advice for earlier (thanks for the help, by the way!)

---

### Post by noob_Lance on 2006-03-15
hey pat. if you have msn, feel free to add me (silver_suicide_rider@hotmail.com) for better help then i can give you here. As for the mount... well i changed the mount point in fstab to /media/Internal but it still shows up at hda6.. wth!?! lol

~Lance

---

