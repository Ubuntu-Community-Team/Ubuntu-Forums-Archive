---
title: "Swap/page file partition help urgent"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-06-30
. As of right now, I've got a separate partition of 3gigs where I place my XP pagefile. I was wondering if I could use this same partition for the Ubuntu swap file as well since I'm gonna be running a dual boot. Would there be any problems with doing that or would I need another partition?

Regards

---

### Post by buuntuu! on 2007-06-30
hi darkstar, [this]("http://www.faqs.org/docs/Linux-mini/Swap-Space.html#ss6.2") might help.

---

### Post by Dark Star on 2007-06-30
Thanks btw I am asking can I use the same partition of Page file for Swap .. Will it workk ..  I don't wanna read that plz tell me...

---

### Post by buuntuu! on 2007-06-30
haven't tried it myself, but the howto i linked to states that it will work...
but have a look at the documentation-section too, you're not the first one to try this, i'm sure :)

---

### Post by eewald on 2007-06-30
> **Dark Star said:**
> Thanks btw I am asking can I use the same partition of Page file for Swap .. Will it workk ..  I don't wanna read that plz tell me...

not really motivating for other people to help you :-(

but anyway.here is my guess - windows pagefile requires windows filesystem (ntfs) to operate and linux swap space requires either swap "filesystem" or some linux filesystem to operate. make your own conclusion now.

---

