---
title: "wrong time/date ubuntu + vmware"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by jcolo on 2007-11-12
Hi,

I have run into subtle problems keeping the time/date with a couple of ubunto 6.10 server I have for development with in a vmware container. The important point in this comment is I am using multicore HW, in my case AMD64.

After a lot of reading and trying many things (  including ntp on cron every hour) I found a solution in vmware site.

These are the links that point to the solution.

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2039](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2039) [http://kb.vmware.com/selfservice/dynamickc.do?externalId=2041&sliceId=1&command=show&forward=nonthreadedKC&kcId=2041](http://kb.vmware.com/selfservice/dynamickc.do?externalId=2041&sliceId=1&command=show&forward=nonthreadedKC&kcId=2041) 

apparently the problem comes from vmware running each instance at random in any of the cores. The mechanisms for keeping sync get nuts this way as sync signals from one cpu and the other will differ.

The solution is forcing each ubuntu instance to run always from the same core as to maintain a congruent  sync signal.

It worked for me and it is here for any body with similar issues. 


Cheers.

JCG

PD: Intels ... same problem. More cores more problems :)

---

