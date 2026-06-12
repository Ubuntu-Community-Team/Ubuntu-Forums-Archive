---
title: "mdadm zero the superblock"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-04-10
I received a "letter" at boot from root@localhost.

It said that I MUST (emphasis theirs) 

zero the superblock before activating the autostart feature.

and

Do not start RAID devices automatically.

mdadm--zero-superblock /dev/xxx

and

dpkg-reconfigure mdadm

Please tell me if /dev/xxx would be /dev/hda OR /dev/hd0

also, tell me what has happened to my newly minted Breezy Badger after 10 hours of downloads.

I didn't see any info that I had started the RAID automatically. Heck! I've only got a used 40gig hdd, anyway!

---

### Post by Mark_in_Hollywood on 2006-04-17
Success!

Upon updating Breezy via Synaptic, the problem was resolved without modifying one single file! It was about 145 meg of download.

---

