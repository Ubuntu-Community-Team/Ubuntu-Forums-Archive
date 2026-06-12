---
title: "partition sizes!"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by fleg123 on 2005-10-06
hey, i am installing kubuntu on my lappy, which has a 60 gig HD. I gave 30 gigs to windows xp (i need it for school) and the remaining 30 will be for kubuntu. I am making 1.1 gigs of that 30 for the swap. I then need to make 2 more partitions. 1 for the root and 1 for /home (i want to do that). 

The question is, how big should i make each of those last two partitions for linux? How much is necessary for / (root) and how much should i use for /home? 

Please help!!!!1 I am new and I haven't been able to find anything definitive on this!!!! 

Thanks a ton! Sorry for posting in Ubuntu forums, but i figured sizes should be about the same for this and kubuntu... and no one is on the kubuntu forums.

---

### Post by heimo on 2005-10-06
Welcome to Ubuntuforums! :) (btw, kubuntu==ubuntu, we are the same distribution)

There is no definitive answer to your question, but something like 5-10 GB for / partition should be plenty. After default install something like 2GB or under is used, but / contains also directories like /var and /tmp and you should have some disk space for those. If I had 30GB for / and /home, I would probably divide it to 6GB and 24GB.

If you format your windows partition using fat32 (instead of ntfs) you can use it as additional space (for example for multimedia) - NTFS for Linux is readonly (there's a way to use it as read/write, but it's a bit risky).

---

### Post by fleg123 on 2005-10-06
thanks a ton =)

After i got no reply for 30 minutes i just did it

i converted the nfts to 25 giving me 35 for linux

i used 7 for /
1.3 for swap
and 26.7 for /home

that basically coincides with what you said... at least i wasnt way off in making them around those proportions.

thanks

---

