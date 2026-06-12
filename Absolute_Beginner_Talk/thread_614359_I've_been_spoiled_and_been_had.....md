---
title: "I've been spoiled and been had...."
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by whitespy9 on 2007-11-15
I installed Gutsy over the past weekend and once again fell in love with Linux. Spent hours upon hours getting everything installed/configured to my liking and then an update rolls out and BAM! 

"Kinit: can not locate image" blah blah. My system will not boot.

So I go and install Dapper (6.06), spend hours getting everything installed/configured to my liking.

I'm completely dissatisfied now that I've seen and used Gutsy and very impressed with it.

Is there a way to roll with both versions and have Dapper as a fall back in case my system goes boom again? 
Is there a way to safe guard myself against Gutsy doing to shat again?

Dual boot is the only thing that comes to my mind.... Any help or suggestion?

Does anyone really use Dapper after using Gutsy?

---

### Post by Paul820 on 2007-11-15
Why did you not come and ask for help on here when it went *BAM* :) ? Most, if not all things that go wrong can be fixed.
Yes you can dual-boot two distros at the same time.

---

### Post by LaRoza on 2007-11-15
I have multiboot 14 distros (and XP) on a single computer. Dapper is still used by many who want LTS.

---

### Post by dfreer on 2007-11-15
Dapper should be a lot more stabler than gutsy, so it isn't a bad idea to keep dapper around if you need the stability (another idea would be to install debian or another older distro if you want rock-solid stability).

You can dual boot, and to save on hard drive space (as well as keeping user preferences relatively the same), you could create 3 partitions: one for gutsy, one for dapper, and one for your /home. Mount /home in both OS, and all of your files will be accessible from both.

Depending on where you install software and how much you install, you could give each OS partition approximately 5-10 GB's of space. Check how much space you are currently using and make an educated guess on how much space you'll need.

In doing this, you can "potentially" run into conflicts, so decide whether this solution is worth it. There are more advanced ways to prevent conflicts, but it requires patience, forethought, and allocating slightly more hard drive space (I'm guessing roughly 1-2 GB's more).

---

### Post by whitespy9 on 2007-11-15
no internal support from Ubuntu being that it is two of the same type of distributions? 


> **LaRoza said:**
> I have multiboot 14 distros (and XP) on a single computer. Dapper is still used by many who want LTS.

---

