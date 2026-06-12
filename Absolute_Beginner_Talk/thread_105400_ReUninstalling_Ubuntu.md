---
title: "Re/Uninstalling Ubuntu"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by raublekick on 2005-12-18
I have some free time now that the semester is over, and I want to fix all the stuff I've messed up in Ubuntu. I think the best course of action is just a nice reinstall since the problems I've created are aplenty. 

I need to backup my home directory, and probably sources.list, anything else?

I'm dual booting with Windows XP, so I'd really like to keep that intact, but if I just overwrite the Linux partitions on the install, will Grub install over itself correctly? Is there another step I need to take instead?

---

### Post by bscbrit on 2005-12-18
If you have a separate /home partition then you can re-install ubuntu without overwriting the data saved on it.  If you haven't, you might want to consider doing it for your next installation.  But also backing it up provides you with another level of safety (and gives you a nice warm feeling....).  If you have some specific settings in /etc you might want to back it up as well.

Ubuntu will create a new grub which will [should!] recognise your Windows partition, but will overwrite the current grub.

---

### Post by raublekick on 2005-12-18
Ok cool. Thanks a lot. The Grub issue is what's really scaring me. I have /home as its own partition, but I'm going to back it up on my second drive anyways, because one of the problems I created is that I thought I set the partition sizes for what would be optimal, and I was wrong :)

I gave / 15 gb, but only used 2, but I gave /usr 6gb and it's almost filled. /home is fine because I don't keep my music and stuff in it. Granted, I could resize the partitions, but like I said I have compounded many issues onto my computer hehe.

---

### Post by aysiu on 2005-12-18
Grub will reinstall itself--don't worry.
I don't see why you would need a separate /usr partition.
A separate /home partition should be sufficient.

---

