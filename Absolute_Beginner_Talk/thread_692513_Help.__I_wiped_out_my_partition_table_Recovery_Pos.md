---
title: "Help.  I wiped out my partition table Recovery Possible?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by fokuslee on 2008-02-09
hi I wiped out my partition table by accident 
its a raid drive with NVraid 
is it possible to recover the partitons? 
with raid setup where is the MBR is it still good?
i am looking at free and commercial way to do it
please help

---

### Post by LaRoza on 2008-02-09
You can use Testdisk.

(See the link in my sig)

---

### Post by fokuslee on 2008-02-09
looks promising im looking into it
since my drive is on nvraid should i worry about dmraid?

i used testdisk on knoppix which come with dmraid
i had 2 partitions on my raid array 
boot -OS
personal data
i was able to recover the parition with all my personal  file collection
i can't recover the boot partition but i shouldn't be greedy


for those who have the same problem
knoppix 5.1
cd /usr/lib
ln -s libntfs.so.10.0.0 libntfs.so.9
-testdisk /dev/mapper/<raid_array>

---

