---
title: "SMART Data &amp; Self Test, 2 attributes failing (Temp, Current Pending Sector Count)"
date: 2019-05-09
forum: Apple Hardware Users
---

### Post by kzqx on 2019-05-09
Hi, I've only been using Ubuntu for a few months on 2013 Macbook air and it's been going well. Today I opened the Drive utility thing and noticed a little label that said "2 attributes failing", after some googling I figure out I need to open SMART data & self-test and I'm greeted by a worrying site.
 


Almost every attribute is listed as at least having failed in the past. As mentioned in the title 2 are listed as failing, Temperature and Current Pending Sector Count. Attribute-17, Attribute-169, Attribute 173 are the only 3 that are listed as OK.
 


I don't really understand what this all means but my attempts at researching suggest this machine is toast. Any information about how I can prolong it's life would be appreciated, or perhaps just information to help ease it's passing.
 

Also sorry if this isn't the place for this post, or if I've done something else wrong.

---

### Post by howefield on 2019-05-09
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by TheFu on 2019-05-09
SMART data is only about the disk and, perhaps the cable to the disk. It could fail any time, but without actually seeing the report, I won't guess.  Use smartclt to run a long test. That should take 2+ hrs. Come back later and view the report using smartclt.

The machine might be, probably is, fine. A failing HDD is hardly a huge problem.

Make certain you have excellent backups and get a replacement disk that is compatible with the machine.  Apple does some funky things. I don't know which HW is and isn't compatible with it.

---

