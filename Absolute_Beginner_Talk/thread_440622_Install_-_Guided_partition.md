---
title: "Install - Guided partition"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by bubka20 on 2007-05-11
I'm installing ubuntu 7.04 desktop on an older Dell which already has Windows 98.  I'd like to keep Windows 98, so during the partition step in install I chose "Guided-use the largest continuous free space".  Then, on the last step before I choose install there is a WARNING message that says "this will destroy all data on any partitions you have removed as well as on the partitions that going to be formatted."
If I choose install at the step will it damage my Windows 98?  Should I choose the "manual" option instead?
Thanks to all..

---

### Post by drowner on 2007-05-11
Yes. Use the manual partition!

---

### Post by bubka20 on 2007-05-11
Ok I chose the "manual"  option and I created a new partition with 2977mb of free space that I have.  What should my mount point be? 
thanks

---

### Post by drowner on 2007-05-11
I highly recommend you use this site: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It is an excellent guide through a manual install, which retains your windows partition.

---

### Post by Billy McCann on 2007-05-11
bubka20,

You'll want to mount to / .  But ...

You're giving Ubuntu less than 3 Gig?  I think that's somewhere around the very bare minimum.  I myself have given around 7 Gig to my root partition partition alone and Ubuntu is using ~60% of that (about 4 Gig).  That's not even counting the data I have on my /home partition.  

Trust me.  You want to give Ubuntu more than what you're giving it.  If not, you may find yourself not able to sign in to your account, if perchance the partition fills up on you.  

Once you decide on a size, mount the partition to / .  

I assume you're not creating a separate /home partition?  It really is a good idea to.  I mean, Gutsy will go beta in what ... 4 months, if everything goes as planned?  You don't want to lose all your application settings, music, etc in a botched upgrade, do you?

Also, if you find that Ubuntu runs a little slowly, try Xubuntu.  It's what I run on my laptop.

---

