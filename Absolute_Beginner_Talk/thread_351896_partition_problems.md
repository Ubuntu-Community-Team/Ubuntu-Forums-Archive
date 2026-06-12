---
title: "partition problems"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by dhutner01 on 2007-02-02
I recently tryed my first my first linux distrobution, ubuntu 6.10, and I installed it through the install menu and gave it a decent partition.

My problem occured when i switched back to windows xp it formated my hard drive automatically, and when I checked the hard drive space, it says I only have 60 GB free on a 200 GB hard drive.  When I restart my computer the partition manager doesn't come up and I'm just not sure how to get to my ubuntu partition.

---

### Post by punx45 on 2007-02-02
are you intending to dual boot or just read the partition through windows?

if dual boot:
do you mean grub? (the thing that lets you chose which OS to boot into at boot time) then you may find yourself in a bit of a pickle.   ive read that if you dual boot, you have to start with windows first then do the other OS, because Windows overwrites the master boot record, no matter what else is there, and i believe that happens to be where grub lives.

if you just need to read the partition through windows:
the linux partition was probably made in the ext3 format. Windows cannot read this by default, but there are some drivers available to enable it to do so.  Unfortunately, I am Windowless, and do not know where to direct you for that step, but i am sure someone else will soon.

---

### Post by dhutner01 on 2007-02-02
yea all I did was format my hard drive and restored the original windows xp that was installed on my computer then I installed ubuntu, then when I switched back, using GRUB, it automatically went to the system recovery mode and formated my hard drive again, leaving only like 60 GB and now when I start up my computer I don't get the GRUB menu

---

### Post by punx45 on 2007-02-04
hmm.. so the drive has been wiped a couple times now? so you wont have a problem starting over again?

I would start over from the beginning and install windows first, then ubuntu.   and [read these guides]("http://www.psychocats.net/ubuntu/index.php") before you do.

especially the 'Plan Partitions' guide.

---

