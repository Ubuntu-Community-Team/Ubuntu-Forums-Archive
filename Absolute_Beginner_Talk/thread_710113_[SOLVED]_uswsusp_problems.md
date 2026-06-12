---
title: "[SOLVED] uswsusp problems"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by alpharavin on 2008-02-28
I am having a problem with uswsusp and the regular Ubuntu hibernate functions.  Whenever i try to hibernate or use s2disk, the system will not shut down, it just hangs on a black screen with a cursor that blinks at me almost mockingly and I cant do anything except a hard reset.  I have had this problem ever since installing the fglrx drivers.  I have tried editing my shutdown method to shutdown and platform and both lead to the same blank screen.  
Any help on this issue would be appreciated greatly.

Dell Inspiron e1705
Intel Dual Core processor
1 Gb ram
ATI Mobility™ Radeon® X1400 256 mb

---

### Post by jw5801 on 2008-02-28
fglrx doesn't play nicely at all with the hibernate and suspend routines. The only way I've found to get suspend and hibernate to work is using the open source ati drivers. It's unfortuneate but you may have to weigh the pros and cons of proprietry drivers vs. suspend and hibernate.

---

