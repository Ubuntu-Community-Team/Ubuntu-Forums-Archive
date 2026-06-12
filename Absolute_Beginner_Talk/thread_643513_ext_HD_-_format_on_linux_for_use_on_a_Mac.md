---
title: "ext HD - format on linux for use on a Mac?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by missed her show on 2007-12-17
Hi! 

I'm running Ubuntu and want to know if this is possible:

I've gotten an external HD for my g/f for xmas.  She's got a mac with the latest o/s -  Will i be able to setup the External HD on my Ubuntu box,  copy data to it, and be able to give it to her ready to plug into her Mac and use? 


Thanks for the help.

---

### Post by xeth_delta on 2007-12-17
> **missed her show said:**
> Hi! 

I'm running Ubuntu and want to know if this is possible:

I've gotten an external HD for my g/f for xmas.  She's got a mac with the latest o/s -  Will i be able to setup the External HD on my Ubuntu box,  copy data to it, and be able to give it to her ready to plug into her Mac and use? 


Thanks for the help.

You could format the hard-disk in something both, Linux as well as Mac will be able to read and write without any issue, for example vfat. It certainly not the best file system, but it is a possibility.

---

### Post by missed her show on 2007-12-17
> format the hard-disk in something both

What are my other options other than vfat?

---

### Post by xeth_delta on 2007-12-17
> **missed her show said:**
> What are my other options other than vfat?

I suppose you could format in a native Linux and install some extra software in her computer so that she can read the data from Mac. I am not sure how reliable this is, though. If you want to format it in HFS+ (from a Mac) and write on it in Linux, you will have most likely to disable journaling on that HDD.

Have a look at these thread:
[http://ubuntuforums.org/showthread.php?t=425154&highlight=format+hfs]("http://ubuntuforums.org/showthread.php?t=425154&highlight=format+hfs")

---

