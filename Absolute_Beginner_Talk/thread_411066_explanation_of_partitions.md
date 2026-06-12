---
title: "explanation of partitions"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-16
Well, I've been using ubuntu for some time now and am pretty stable with it.
but as I was using it once I noticed a slight change in the speed. 
so, I want to know how much space is in my ubuntu partition. do you know the command?
oh and I want to know what partitions I've made so far considering that I dont' remember :]

I"m also planning to delete my previous windows partition and **maybe** expanding my ubuntu, maybe. please give me words of advice and your opinions if I should do this or not, thanks ubuntu community:D

---

### Post by 23meg on 2007-04-16
> so, I want to know how much space is in my ubuntu partition. do you know the command?
oh and I want to know what partitions I've made so far considering that I dont' remember :]

```
df -h
```

---

### Post by Parasitesss on 2007-04-16
thnkyou

---

### Post by Parasitesss on 2007-04-16
What is that?

> 

john@john-desktop:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on

/dev/hda2             4.2G  3.0G  994M  76% /

varrun                252M   80K  252M   1% /var/run

varlock               252M  4.0K  252M   1% /var/lock

udev                  252M  128K  252M   1% /dev

devshm                252M     0  252M   0% /dev/shm

lrm                   252M   19M  234M   8% /lib/modules/2.6.15-28-386/volatile

john@john-desktop:~$



what do each of them stand for? the varlock and Irm..

---

