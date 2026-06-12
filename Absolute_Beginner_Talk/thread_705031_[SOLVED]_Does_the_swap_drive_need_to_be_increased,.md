---
title: "[SOLVED] Does the swap drive need to be increased, if I increase my RAM?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by BOZG on 2008-02-22
I read a suggestion that it's a good idea to have the swap about twice the size of your physical RAM so I set my swap to 2gb.  I'm after increasing my physical RAM from 1gb to 3gb so should I increase the swap size or should I be fine as it is?

---

### Post by Sinkingships7 on 2008-02-22
a 2 GB swap will be just fine, and the fact that you're adding more physical ram only makes it more okay, as the swap is only used when you run out of physical ram.

---

### Post by uberlube on 2008-02-22
Good question.

---

### Post by InfinityCircuit on 2008-02-22
The only qualifier on that statement is if you need to hibernate, in which case you must increase your swap size to greater than 3 GB.

---

### Post by mbsullivan on 2008-02-22
> The only qualifier on that statement is if you need to hibernate, in which case you must increase your swap size to greater than 3 GB.

Although it may error out with < 3GB of swap if you want to hibernate, there are ways around this. Also, since you're not likely to be using > 2 GB @ time of hibernation, this issue may never come up. It's not a definite.

But yes... in recent times, setting swap = to size of RAM is a pretty good idea, since it's really only heavily used for hibernation. I wouldn't rush to change yours, though, even if you hibernate your machine. 2GB should be fine.

Mike

---

### Post by BOZG on 2008-02-23
Thanks a lot everyone.  I don't hibernate so I guess there's no need to worry about it.

---

