---
title: "Help with Partitions: How big?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by qureshia49 on 2007-10-22
I am  really really a newfie. I am just about to install Ubuntu V7.10. The partitions that I have created are as follows:

/Root        25GB    

/Swap       4GB

/Boot         2GB.

I would appreciate from fellow novice & expertise if this is right and I should go on with the install. Please respond with your feedback with improvement suggestions.

Thank You

Ash

---

### Post by kerry_s on 2007-10-22
> **qureshia49 said:**
> I am  really really a newfie. I am just about to install Ubuntu V7.10. The partitions that I have created are as follows:

/Root        25GB    

/Swap       4GB

/Boot         2GB.

I would appreciate from fellow novice & expertise if this is right and I should go on with the install. Please respond with your feedback with improvement suggestions.

Thank You

Ash

4gig swap is to big, 1gig is enough, how much ram do you have?
boot is to big to 512mb is good.
root holds your system so 25gig is good.

you actually don't need a separate /boot at all, unless your going to use xfs for your file system and want grub.

/Root        25GB   
 /Swap       1GB
maybe a separate /home
/home    5gb

home is were your settings, doc's and files are kept.

---

### Post by Sef on 2007-10-22
> /Root 25GB

/Swap 4GB

/Boot 2GB.

I would do it like this:

/(root) 10 GB (more than enough)

/home 15 GB (in case your root has problems, your files will usually be safe.

/swap 1 GB (If you have a GB or more or ram, then swap really isn't needed, unless you           are into gaming or movie editing.)

/100mb (Why do you want a separate boot? It is not needed.)

---

### Post by kerry_s on 2007-10-22
yeah i usually only use1, just / root unless i'm messing around. :)
like on this install i'm playing with xfs so i added a /boot cause i hate lilo and i added swap cause i was trying something that needed 1.

but yeah, if you use external drive to back up your stuff you can get away with just 1 / root partion. i don't trust internal drives, cause it's usually the whole drive that go's bad.

---

### Post by mivo on 2007-10-22
I'm with Sef.  10 GB for /, 1-2 GB for swap, rest for /home.

---

### Post by Lfrb on 2007-10-22
Is it a laptop ?
Because if you want to hibernate, the size of your /swap must be the same size than your RAM.

--
Louis-Francis

---

