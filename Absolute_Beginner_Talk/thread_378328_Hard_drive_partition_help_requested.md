---
title: "Hard drive partition help requested"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Bideshi on 2007-03-07
We are trying to install Ubuntu 6.06 onto our new desk top which was brought pre-loaded with Windows XP on 25 GB of a partitioned hard drive.  We are in Bangladesh and when we got to the partition hard drive installation stage the power and our UPS failed.  We had tried to set aside 256 MB of the hard drive for a swap space when this happened by setting up empty space on the section of the hard drive (55 GB) we had reserved for Ubuntu.  We went to the manual partition option of the installation because the options for where to install Ubuntu were confusing and were not what we had expected to see.  We had assumed there would be the option of installing in on hard drive c or d.  When we turned the computer back on, we found that we could not resize this section of our hard drive.  We tried via the system tool (g-partition) and via the installation procedure.

We want to dual boot Windows XP (for a few applications that are not Linux compatible) and Ubuntu but are a bit stuck about what to do next.

How do we:
1. get rid of the 250 MB empty space on the 55GB section of the hard drive?
2. set up the 256 MB swap space?
3. what is mounting?

Any help would be gratefully received, as you can see we are clueless.  We have read the forum help documents, which are good but do not seem to address our specific problems.

---

### Post by buuntuu! on 2007-03-07
hi there, welcome to linux!

i hope, gparted was not already WRITING anything when your power failure happened, as this could have really messed up your HD! as long as you had not already hit the "apply" button nothing bad should have happened.
a partition which is active (mounted) cannot be manipulated by gparted. you have to unmount it before you can apply changes.
the swap space is set up during the install, follow psychocats easy[instructions]("http://psychocats.net/ubuntu/installing") on how to partition your disc.
i hope this helps a bit,
buuntuu!

---

### Post by Bideshi on 2007-03-07
Thanks Buuntuu,

We have now successfully installed Ubuntu.
The psychocats helpsheet was very useful.

---

