---
title: "[SOLVED] X not starting"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by arvevans on 2007-09-29
Yesterday I did an on-line upgrade from fiesty to gutsy.  Now when I reboot it comes up with a text login.  After logging in I can enter "startx" and everything works just fine with X windows.

Where should X be launched?  There are several places I can put this command, but I want to do it right to avoid potential problems later.

Thanks,
Arv

---

### Post by Sheepish on 2007-09-29
Once your in, and running x, you should be able to go to "services" or "startup" or something, lol. im not at my linux comp so i cant see for sure but you can add processes to start and in what order...

hope this helps:confused:

---

### Post by arvevans on 2007-09-29
No X-starter in System/Administration/Services/Startup

Any other ideas?

I can put it in one of the /etc/rc.??? files but which one is the correct place?

---

### Post by Sheepish on 2007-09-30
if you use the same command, that you use to start x in the first place, there is a way to add a new command, you might need to use sudo if the problem is with login. Privilages may have something to do with it as well. 

God this thread got buried by new threads since last night.

When im back at home ill have another look, then ill private message you.

Joe

---

### Post by arvevans on 2007-10-02
Thanks for the help, but it is resolved now. 
 I gave up and reloaded XOrg.  That is a bit brutal but it did the job.

Arv
_._

---

