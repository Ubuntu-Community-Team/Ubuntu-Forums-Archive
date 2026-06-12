---
title: "dual booting problem"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Fayte2071 on 2007-09-06
Ok, I read all the other ones and haven't really found the one with my problem. I'm dual booting windows xp and ubuntu, both on different hard drives. Now when I start up my computer, i get the grub loader (it shows which OS i'd like to load). That all works, but when i hit on ubuntu, 98% of the time it won't load. It'll say "Loading, please wait" but freeze on that screen. That other 2% of the time it'll work perfectly. This is very irritating, how can i fix this so it'll always load?

---

### Post by oilchangeguy on 2007-09-06
> **Fayte2071 said:**
> Ok, I read all the other ones and haven't really found the one with my problem. I'm dual booting windows xp and ubuntu, both on different hard drives. Now when I start up my computer, i get the grub loader (it shows which OS i'd like to load). That all works, but when i hit on ubuntu, 98% of the time it won't load. It'll say "Loading, please wait" but freeze on that screen. That other 2% of the time it'll work perfectly. This is very irritating, how can i fix this so it'll always load?

how long has this been going on? and what did you do to the computer prior to this problem occuring?

---

### Post by Fayte2071 on 2007-09-06
It's been going on since I installed ubuntu. I've reinstalled ubuntu a couple of times now, thinking it was just a bad install.

---

### Post by zeehat on 2007-09-06
That sounds like it could be a hard drive issue.  How old is the drive? Size/ speed?

---

### Post by Fayte2071 on 2007-09-06
The drive is maybe a year or so old. it's a 80GB harddrive, not sure the speed, but it's not horrible. Like right now I'm on ubuntu, my previous posts were on windows. I finally got on ubuntu

---

### Post by cubeist on 2007-09-06
next time grub comes up hit "e" and remove the "quiet" tag (I'm pretty sure quiet is the option you want, although it could be nosplash... maybe someone can back me up on this), anyway, removing this option will show the progress as the system loads and perhaps you can see what is causing the problem (wireless, usb, etc.)

---

### Post by cubeist on 2007-09-07
Just a quick clarification to my previous post.  In the boot menu change "splash" to "nosplash" and the system will display line by line the progress of the boot.  Hopefully you can see if anything is causing it to hang.  I can't remember what the "quiet" option does... I will try that in my next boot.
Good Luck
> **cubeist said:**
> next time grub comes up hit "e" and remove the "quiet" tag (I'm pretty sure quiet is the option you want, although it could be nosplash... maybe someone can back me up on this), anyway, removing this option will show the progress as the system loads and perhaps you can see what is causing the problem (wireless, usb, etc.)

---

