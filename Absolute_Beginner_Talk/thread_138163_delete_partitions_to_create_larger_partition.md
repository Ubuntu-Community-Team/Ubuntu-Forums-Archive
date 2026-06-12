---
title: "delete partitions to create larger partition"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by multios on 2006-03-01
I have 3 small partitions (hda5, hda6, hda8) that I would like to use for Breezy. 
I know it is a weird *lay-out*, but I needed hda7 for a /home partition (I needed its size). 
My problem is that I have pclinuxos on hda9,10 and Slack on hda11. If I create a new partition with 5 and 6, will that change the hda number for pclinux and slack? 
I am afraid they won't boot or will their partition numbers stay the same and the *new* partition be numbered hda12?
If I do repartition, will it mess up the mbr? 
Thanks. 
multios

ps- I had Hoary and now want to get back to either Breezy or Dapper.

---

### Post by jeremiebergeron on 2006-03-01
When you delete and create partitions all of your partitions that you leave alone should keep the same partition numbers. Although, depending on how you do it the order of the partitions may change (i.e. 5,7,6). Partition editors will complain about this but it shouldn't mess things up.

---

### Post by multios on 2006-03-01
Ok, thanks. 
I will give it a try.

---

