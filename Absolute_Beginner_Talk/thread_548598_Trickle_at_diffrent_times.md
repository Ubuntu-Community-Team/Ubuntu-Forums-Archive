---
title: "Trickle at diffrent times"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by gav616 on 2007-09-11
My ISP throttles if i download more then 750MB between certain times,

what i need to do is limit aMule upload to;

15kb 1600 to 0400
30kb 0400 to 1600

how do i schedule this with Trickle? cron? if so, how?

Thanks.

---

### Post by Skrynesaver on 2007-09-13
I suspect you'll have to put 2 tc commands into cron, how to write the tc commands is another question entirely, something like the following would limit your connection absolutely

```

tc qdisc add dev eth0 root tbf rate 15kbit

```
put this in a script and then run crontab -e as root and add the following line
```
59 15 * * * <filename> 
```
and a similar line to reset your rate to run at 4:01

But you probably only wish to restrict a certain type of traffic.  Much man page reading I fear. 
 BTW, if you work this one out I'd love to know the incantation that does it.:lolflag:

---

