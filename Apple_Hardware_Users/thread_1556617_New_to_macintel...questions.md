---
title: "New to macintel...questions"
date: 2010-08-19
forum: Apple Hardware Users
---

### Post by airtower on 2010-08-19
Hey all, I decided to retire my 7 year old Dell P4 and cash in on a MacPro 3,1 that a buddy of mine is selling. I'm super excited, but I have a few questions partly because it seems some of the documentation on here is a bit out of date. I am planning to run Lucid x64.
 
1 - I don't have any use for OSX, but I've read that completely removing it is not recommended since you may need it for Apple firmware updates. Is this still the case? Is Apple still releasing updates on a two year old system? Storage space isn't really the issue in as much as tidiness and more importantly simplification of the boot process....I've never been a fan of dual booting, but it's been about 12 years since I've done it and that was Windows 98 alongside Red Hat.
 
2 - The system has the optional GeForce 8800 GT installed. Will this work ok with the standard restricted drivers? I plan to run compiz as well.
 
3 - The system is coming to me with a 750gb hitachi drive and two 500gb WD drives. He has them currently configured in a software RAID0. I have another 500gb WD drive that I would like to use to set up a RAID5. The system does not have the Apple RAID card, and from what I understand, it's a waste of money due to poor performance. Are there any third party cards that are supported by Ubuntu that will work in the MacPro? I have zero RAID experience and honestly don't know much about Mac's. The RAID will not have any bootable partitions, that will all be reserved for the 750gb.
 
TIA for any advice! The computer should be at my door next week some time.

---

### Post by liquidfunk on 2010-08-19
As long as you have two same size partitions you can do software raid on them. So 2x 100Gb /home folders on Raid 1 will work. I wonder if you'd benefit from using LVM on those drives too?

[HTML]http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/ch-software-raid.html[/HTML]

---

