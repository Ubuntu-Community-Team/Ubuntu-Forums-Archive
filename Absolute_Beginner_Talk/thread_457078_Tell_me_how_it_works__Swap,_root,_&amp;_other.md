---
title: "Tell me how it works?  Swap, root, &amp; other?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-05-28
Numerous posts and tutorials exist advising how to partition a drive for Ubuntu, but not why.  For example, one is told to allow 2GB for the installation, and 3 x RAM for the swap partition.  

QUESTION 1:  If space is not an issue, is there an advantage to making the 2GB partition larger, anticipating future releases of Ubuntu?  Is other software installed into that same partition?  What is the default name of the installation  partition?

QUESTION 2:  Are user files stored in the Ubuntu installation partition?  If not, where are they stored, and what is the default name of that partition?

QUESTION 3:  Is it correct that for 2GB Ram the swap partition should be 6GB?  If space is not an issue, is there an advantage to making the swap partition larger? 

Yep.  I am totally new and don't have a clue.  Thanks in advance for any help.

---

### Post by dptxp on 2007-05-28
Numerous posts and tutorials exist advising how to partition a drive for Ubuntu, but not why. For example, one is told to allow 2GB for the installation, and 3 x RAM for the swap partition.

QUESTION 1: If space is not an issue, is there an advantage to making the 2GB partition larger, anticipating future releases of Ubuntu? Is other software installed into that same partition? What is the default name of the installation partition?

[COLOR="Green"]2 GB is Fine, I use 2 GB, you can change it later with GParted, just keep it at end of the drive[/COLOR]

QUESTION 2: Are user files stored in the Ubuntu installation partition? If not, where are they stored, and what is the default name of that partition?

[COLOR="Green"]By default they are stored in the home partition in the USER file (everything is file). By default, unless you have made a /home partition, the home partition is same.
You can save anywhere you like, in any partition, some formatting may not allow access.[/COLOR]

QUESTION 3: Is it correct that for 2GB Ram the swap partition should be 6GB?
[COLOR="Green"]NO[/COLOR]

---

### Post by nvteighen on 2007-05-28
1) For the "root" partition (install partition), you should use more than 2 GB (that's the minimum!). I've been told to use between 10 - 15 GB, because this partition is also for installed software, not only for the system.

2) The "home" partition is where personal data of users is allocated (this means **all** /home directories are placed there).

3) The swap partition is generally said that should be as big as your RAM. No more swap is needed; if you use more, you'll realize you're wasting your space. That's the only reason, but if you want a 40 GB big swap partition, just do it ;-)

---

### Post by mills on 2007-05-28
1) for the initial install you'll need to have 2GB spare but you'll definitely want more than that so you can add your ow programs, i have 20GB in my root partition and thats plenty.

2) if you make a home partition then personnel (user?) files are stored there, 
3) as for swap you'll want twice your ram but no more than 2GB, i have 512mb ram and 1gb swap but I've never seen my swap use more than 512mb

---

