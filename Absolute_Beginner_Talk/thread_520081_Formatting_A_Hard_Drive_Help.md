---
title: "Formatting A Hard Drive Help"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by BuffaloBeagle on 2007-08-07
I am having some issues with my computer at the moment.  I need to format my hard drives through the Live CD.  I am booted in the LiveCD right now and i have 2 harddrives that i need to format.  One is a 74GB 10000RPM WD SATA Raptor drive and the other is a standard 80 GB 7200RPM IDE Drive.  How do i format the drives through Ubuntu and what type should i format them to.  One will be where i install Ubuntu but i want to format both before hand and i want to format the IDE one for storage and the raptor for Ubuntu.   I hope that people can understand what i am typing and please i need someone to help me with this,

Thanks,
BuffaloBeagle

---

### Post by bodhi.zazen on 2007-08-07
I would format them with ext3, although there are other fine file systems.

You will need 2 partitions for Ubutnu, / and swap. Swap = RAM X2, max 1 Gb, unless you have a laptop and plan to hibernate , in which case swap = RAM

You can consider a separate /home partition.

You can format with gparted, it is on the live CD

---

### Post by cobrn1 on 2007-08-07
Hi

Maybe think about a setup like this:

HD1 - partition1 - ext3 - / (root)
       - partiton 2 - swap - swap (1gig or so)

HD2 - partiton 1 - ext3 - /home

---

