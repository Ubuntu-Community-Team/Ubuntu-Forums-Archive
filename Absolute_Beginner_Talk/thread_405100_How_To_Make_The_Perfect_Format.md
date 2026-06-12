---
title: "How To Make The Perfect Format?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by ciarals on 2007-04-09
Hi!
I have a question. When the version 7.04 will arrive, I'll want to format my laptop where now is installed only ubuntu 6.10 and then install the new version. 
What is the better method to format my HD? Is there an application that can format perfectly my pc so then, after rebooting, I can install ubuntu in a super-cleaned HD?
Another little technical question: formatting many times can damage an HD?
Thank you so much for your answers.

---

### Post by jhenager on 2007-04-09
Fiesty is due out in April, but I don't know the exact day.

As for the perfect format, you don't have to do anything if you want a super-cleaned HD. You just select the option to 'Erase and use the entire hard disk' during install.
Formatting a disk won't damage it any more than normal reads/writes. It would be a waste of time to do it more than once unless you just like to watch the sector/block count incrementing.

---

### Post by ciarals on 2007-04-09
There are voices of the 19th of April for the release date. 
By the way, I was asking this because I thought that the option you said me (and that I always use) didn't format perfectly the HD... How can it format AND install ubuntu in only 30 minutes? The format process should take more time... or not?

---

### Post by jvc26 on 2007-04-09
If I am right, doesnt the standard Ubuntu format merely cause the computer to forget where all the data on the Hard Drive is, effectively rendering it clean (as the computer doesnt think there is any data on there, and writes over the free sectors) This doesnt take very much time as it just erases all the computer's data on the handles of these sectors, and then it can install to what it now sees as a completely empty drive, even if on the disk surface there is still untagged data on it.

You may well be able to do a 'full' format option perhaps, which writes over the entire disk surface with random 1s and 0s thus rendering all information which used to be on the disk irretrievable. I dont think however it is possible to return to the factory state of NO DATA on the disk, as there will always be something once it has been used. This may well be available using some form of tool such as the GParted Livecd.

Il

---

### Post by ciarals on 2007-04-09
Thanks for the answer. So, in other words, the option 'Erase and use the entire hard disk' during install is the best (and fastest) way to format my HD?

---

### Post by jem7v on 2007-04-09
Pretty much. It only takes a few minutes.

When deciding on your partitioning scheme, by the way, it would be a good idea to have a seperate home partition. It makes upgrading nicer.  This talks about making a new home partition before you upgrade, which might be worth doing: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

