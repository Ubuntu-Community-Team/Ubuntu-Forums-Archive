---
title: "Huh? Flash drive probs, HELP!"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Archoniam on 2007-08-02
I'm having a prob with my flash drive. Does anyone know how to mount a SanDisk Cruzer 4GB (not gonna make much difference) that somehow is not recognized, was on sda def /dev/sdb1, labeled LINUXKEY, and with an unknown filesystem? and what is the common filesystem on them? Here's another question: Is there a terminal history for whenever? Because if i can get to that, i can probably get to my drive filesystem type so i can mount the #@*$ thing.
(Note: I just played russian roulette with a Nerf dart gun and three other people who, for the most part, ended up like me.)

---

### Post by apswartz on 2007-08-02
This review seems to suggest problems with that flash drive and linux...
[http://www.epinions.com/content_342485012100](http://www.epinions.com/content_342485012100)

---

### Post by john.nicholls on 2007-08-03
Flash drives usually come with the FAT32 file system.

Look at /var/log/syslog to see whether the drive is recognized; check any references to SCSI.

---

