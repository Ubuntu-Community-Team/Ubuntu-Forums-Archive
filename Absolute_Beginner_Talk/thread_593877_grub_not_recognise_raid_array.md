---
title: "grub not recognise raid array"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-10-27
I have windows setup on a 2 drive stripe.
I just installed ubuntu on a second drive. GRUB did not recognize the windows installation how do I add it manually

---

### Post by bigmonmulgrew on 2007-10-27
bump

---

### Post by vgrisham on 2007-10-27
> **bigmonmulgrew said:**
> I have windows setup on a 2 drive stripe.
I just installed ubuntu on a second drive. GRUB did not recognize the windows installation how do I add it manually

Ubuntu's RAID recognition is weak (and that's the best I can say about it). I've tried hardware, fake and software raid with no success. I hate to be negative, but I don't think at this stage Ubuntu will do what you want it to do (especially if your array is fake or motherboard based). :(

---

### Post by Mondoman on 2007-10-27
However, if you're willing to buy a stand-alone RAID controller card (which has its own advantages over MB-based "RAID"), you can set up a nice system.  I used the same (used) controller card mentioned in an article ([http://www.smallnetbuilder.com/content/view/27840/77/](http://www.smallnetbuilder.com/content/view/27840/77/)) and have been very happy with it under Feisty.  The main problem I've run into so far is that many Linux disk tools can't handle a partition larger than 1TB.

---

