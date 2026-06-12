---
title: "Virtualbox .vdi expanding"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by n3tfury on 2007-09-25
hello good people.  i've been messing with virtualbox for a couple of weeks now and love it.  my host OS is LinuxMint and the guest is Vista Ultimate, both run great.  i understand that the vdi for Vista is dynamic in size, so it will expand if it needs to, but i had about 7% free space left on my linux partition and after Vista was idling for a few hours, Virtualbox showed a disk space error and i was down to no space left on my Linux partition.  

that's alot of room for just an idling system.  anybody know what's going on?  no apps were being run on the Vista box and no torrents, yadda yadda.

---

### Post by n3tfury on 2007-09-26
bumping this because i thought i had solved the issue.  this is still happening.  any thoughts?

---

### Post by jaygo on 2007-10-04
is it definitely the vdi file that's expanding?

---

### Post by hamster_billy on 2008-01-13
The .vdi is dynamic in size in that it will grow as the amount of the virtual disk which is used grows. However, I believe it won't shrink. There is a facility somewhere which shrink it, but for this to work the unused portions of the virtual disk need to be preblanked in a specific way. It isn't the most useful feature out there.

---

