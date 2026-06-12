---
title: "ubuntu live cd  + flash drives and cd drives"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by stroch on 2006-09-23
Sorry if this is redundant, but I am wondering if booting from my ubuntu live cd allows swap files to be written on my hard drive? I booted from live cd and was able to access my flash drive for documents/image files, as well as my cd drive for the same. Knoppix live has a noswap command at the start of booting, but I didn't see the same for Ubuntu (Ubuntu is, in my opinion, infinitely nicer and faster than knoppix...). Just want to check regarding any changes to my hard drive. 

I've never installed linux before, so I don't, I think, have a Linux Swap Partition (type 0x82) which I read in another post that the live cd would use if available. 

Anyone?

---

### Post by b_martinez on 2006-09-23
No ,Ubuntu will not make any partition. This you must do yourself. If you plan on using any Live CD a lot, then it may be worthwhile to free up a half gig or so at the end of the hard drive and make it a swap partitiion. Even the Ubuntu live cd will work better with swap space. If you have over 1 gig ram, I know that with Knoppix you can boot with the 'toram' option, and it runs very fast.
hth
Bill

---

### Post by stroch on 2006-09-23
Thanks so much, Bill. I'm assuming that to free up that extra 512 MB of hard drive space, I will have to either use partition magic or repartition via a re-installation of XP?

---

