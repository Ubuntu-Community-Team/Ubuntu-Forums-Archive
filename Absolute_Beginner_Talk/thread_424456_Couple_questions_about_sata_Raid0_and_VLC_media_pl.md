---
title: "Couple questions about sata Raid0 and VLC media player."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by BeastlyKings on 2007-04-26
Statement:
I am going to be building a new computer as soon as the parts arrive. I have the floppy for the sata drives and also for the raid0.

Question #1:
Can I install two 120Gb HDD set up in raid 0 configuration?
This raid install would be a hardware raid not software, would it be easier to do it software style?
Can Ubuntu 7.04 do a software raid with sata drives?


Question #2:
I want to install VLC media player not only on my new machine but also on my other ones, all running 7.04.
How come I cannot find VCL media player in the "Add/Remove..." section anymore?
If it is no longer supported, why isn't it supported?

---

### Post by Zuph on 2007-04-26
I can't speak to Question 2, but for question 1:

Ubuntu can handle that software raid and the hardware raid equally well.  Depending on your raid controller, though, software will be more difficult and not quite as fast.

Before you set up a Raid 0, though, keep in mind that you are almost halving your reliability (if one drive fails, you lose ALL YOUR DATA), but you gain NO PERFORMANCE unless you buy a high-end raid card.  We're talking $350+ for a RAID controller to gain much performance.  The card built into your motherboard or the $40 Promise controller will NOT IMPROVE PERFORMANCE.

See the following:

[http://faq.storagereview.com/SingleDriveVsRaid0](http://faq.storagereview.com/SingleDriveVsRaid0)
[http://www.anandtech.com/storage/showdoc.aspx?i=2101](http://www.anandtech.com/storage/showdoc.aspx?i=2101)

---

### Post by BeastlyKings on 2007-04-26
Hmm... I see.
Well then, I would just go ahead and do RAID 1 instead. But after thinking for awhile I realized that I might not be able to put the second drive in anyway due to power restrictions.

See, this computer I'm building, I'm going to put it in my car as a media station for all my music and whatnot. I have a hatchback, and I'm going to put it in the back and run the monitor cable to the front, whilst controlling it with a wireless mouse and keyboard.
But the restriction comes in because I don't want to buy a big inverter to power all this so I want to keep it sipping power, especially because of the four 8" speakers and one 8" subwoofer.

How much does a 600W PSU pull from the wall and would the fact that I'm running a monitor and nine 8" speakers affect the power output of my inverter to the point where it couldn't power the PC?
Come to think of it I might need a deep cycle battery, the one I have atm is brand new but standard.

What are your thoughts on this?

---

### Post by Zuph on 2007-04-27
A 600W power supply can pull a maximum of about 600W.  Depending on your components, it will usually draw less than 200.  Hard drives will pull about 30 watts when they spin up, but less when they are spinning.

This all depends on the components you plan on using and the inverter you already have.

---

### Post by BeastlyKings on 2007-04-28
Thank you for this info, but do you think I should switch over to a Mini ITX mobo with a DC to DC PSU?

The reason for this is it uses less power, and the case could be more rugged, I live on dirt roads that usually have pot hles and whatnot and I think it might jar loose the CPU and heatsink.

---

