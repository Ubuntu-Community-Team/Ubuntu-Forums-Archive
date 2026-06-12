---
title: "Macbook 1,1 shows 2 linux partitions in rEFIt post 11.04 install, can't boot either"
date: 2011-08-06
forum: Apple Hardware Users
---

### Post by zonker1984 on 2011-08-06
I followed the instructions here: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

to the best of my availability, and now when I boot my laptop up, it shows two linux partitions in rEFIt and both of them hang at the GRUB screen.

I've made sure that GRUB is on the EXT4 partition, and have re-partitioned it multiple times. I've tried 10.04 on it as well with the same result.

---

### Post by zonker1984 on 2011-08-08
UPDATE: I figured out after a little research that the old version of GRUB in my MBR from last time I had done this (back in 2008 ) and used a GRUB repair disc to restore my Boot Camp MBR and then followed the mactel instructions and now it works. I am posting this from 11.04 on my MacBook. Huzzah!!!

---

