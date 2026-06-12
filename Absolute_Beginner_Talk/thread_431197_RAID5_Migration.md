---
title: "RAID5 Migration?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by fellgoog on 2007-05-02
Summary: How to get a new system to recognize & mount an old raid5


Good evening,

I have the following question which - to my knowledge - hasn't been answered here yet.

I had a running 7.04 system (on /dev/hda) with /home on a RAID5 (disks /dev/sda - sdc).

Now I lost the _system drive_. 
I installed 6.06 LTS server on a new one, but it didn't seem to recognize my raid.
I tried to assemble it with mdadm, with the --force flag, I set up a new /etc/mdadm/mdadm.conf, to no avail:
all the response I get from mdadm is
"No devices listed in conf file were found" or alternatively "no devices found for /dev/md0"

All three disks are untouched to my best knowledge, now how can I get them into the system?

Thank for any help!!

---

### Post by Dtree on 2007-05-02
Hi,
I dont know much of anything but Ive observed asking questions about raids containing existing data makes you something of a pariah. 
I have several raids from my windoze box I wanted to migrate but finally gave up.
I think folks are hesitant to give advice where the result could be a loss of valuable data (understandable I guess)
Im just going to wait until I can get another set of drives to bounce everything off (musical chairs so to speak)
Im not suggesting you should do that hehe, just whatever you do...Back it up Back it up Back it up!!!
I do hope your problem gets solved sooner than mine will , Good luck

Dennis

---

### Post by fellgoog on 2007-05-03
True, Raid5 questions seem to be of the more obscure kind.

Still, those disks contain my backups, so it's not data I need on a day-to-day basis. I can leave them lying around until some solution comes up. There's already some great howtos for raid5 that cover building and rebuilding, maybe someone will write one for more obscruer problems.

f.

---

### Post by fellgoog on 2007-05-03
Well. This is now a make or break situation. It turned out, I had bad superblocks on the RAID. Not much to do there, except re-creating it on top of the old raid. There's an excellent description of someone who has been through the same here: [http://www.mail-archive.com/linux-raid@vger.kernel.org/msg05304.html]("http://www.mail-archive.com/linux-raid@vger.kernel.org/msg05304.html"). Right now, the array is rebuilding and I pray the xfs ontop is unscarred.

---

