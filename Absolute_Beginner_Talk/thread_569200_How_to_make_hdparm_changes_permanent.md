---
title: "How to make hdparm changes permanent?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by imnotryan on 2007-10-06
Hey, I've built a silent computer and want the HD's to spin down when not being used...

I put in " sudo hdparm -S 10 /dev/hda "  (it needed sudo or else it said no permission)

It worked and one of the hard drives spun down, however after a restart, it wont do it again so the change was not permanent.

I can not stress this fact enough - I do not know how to find files outside of my home directory or any of that, in fact I'm still shady on going root, so I'll need some pretty step-by-step directions... :(


Now for supplemental question...  Will having the hard drives spin down shorten their lives, harm them, or anything like that?

---

### Post by w7kmc on 2007-10-06
You can enable hdpam in /etc/hdparm.conf

I think the option you want to add is   spindown_time=240

This will spin it down after 20 minutes

---

### Post by imnotryan on 2007-10-06
> **w7kmc said:**
> You can enable hdpam in /etc/hdparm.conf

I think the option you want to add is   spindown_time=240

This will spin it down after 20 minutes

It already had this with a # infront of it.  I deleted the #.  However it will still not power the HD down.

It had 
> # -S standby (spindown) timeout for the drive
#spindown_time = 240

Now it has
> # -S standby (spindown) timeout for the drive
spindown_time = 240

Still no dice.

---

### Post by imnotryan on 2007-10-07
Alright I got the answer from this post

[http://ubuntuforums.org/showthread.php?t=269106&highlight=hdparm+permanent](http://ubuntuforums.org/showthread.php?t=269106&highlight=hdparm+permanent)

---

