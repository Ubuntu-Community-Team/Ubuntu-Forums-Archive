---
title: "Additional disk doesn't show"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by manemannen on 2007-11-07
Bios locates my 2 disks. One is a SATA and one is an Ultra ATA. Both are set as primary drives. Now Ubuntu recognizes the SATA disk where it is installed. The Ultra ATA is a total no show in /dev/ - whats wrong?

Output from "sudo fdisk -l" is:

/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris


Any ideas?

---

### Post by ofb on 2007-11-07
There's a bug or two with IDE right now.

You can probably get the drive to show up with this fix,
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581/comments/25](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581/comments/25)

...but I don't recommend it.

Short version of a long story is there's a number of IDE device issues right now that are probably related. So while that fix allowed me to see my CDRW again, that merely moved me into the group of people whose burners can read but not burn. Seems like it cured a symptom rather than the actual problem, or problems.

My non-expert advice at the moment is wait for the official patches, rather than start messing with the system.

---

### Post by manemannen on 2007-11-08
ok thanks, the problem isn't critical since my main disk is pretty empty - I just cleaned out the Windows infection and went pure Ubuntu :KS

Hope they solve it otherwise I can put the disk as slave to my CD/DVD (maybe it shows then) although that is not the preferred action.

---

