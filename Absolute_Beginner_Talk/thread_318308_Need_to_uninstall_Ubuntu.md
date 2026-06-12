---
title: "Need to uninstall Ubuntu"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Turbojoe on 2006-12-13
My machine right now has three hard drives. I formatted and installed Ubuntu on to a 30 gig spare drive I had laying around unused. My daughter just had a hard drive failure and I'd like to send her this drive. I tried removing it (physically) from my system and it would no longer boot into Windows XP. From what I understand Ubuntu modifies the MBR. I just did a clean install on the boot drive and finally have it setup the way I want it. I need to replace the MBR but I REALLY don't want to have to do another clean install. I also have Windows XP on the second drive that is staying in the system. Is there any way to transfer this one over? I know enough about computers to be dangerous so I need a step by step procedure for idiots to straighten out my MBR and be able to remove the Ubuntu drive from my system. (She can format the drive when she puts it in her system.) I need to get back to the way things were before Ubuntu. Nothing against the OS. I just don't have the time to spend learning a new OS.


Joe

---

### Post by Fully216 on 2006-12-13
If you have the XP CD, run the recovery console and use the command fixmbr.  That will rewrite the master boot record for the current XP installation.  ;)

---

### Post by Fully216 on 2006-12-13
Also sorry to hear you will be leaving ubuntu.  Hope you will come back someday, and thanks for giving it a try.

---

### Post by Turbojoe on 2006-12-13
> **Fully216 said:**
> If you have the XP CD, run the recovery console and use the command fixmbr.  That will rewrite the master boot record for the current XP installation.  ;)

I had read about that procedure and tried it. However the drive is partitioned and it said it COULD possibly make all partitions unreadable. That scared me off and I aborted. I don't want to lose the info on the other partitions. Am I being overly concerned? 
Thanks,

Joe

---

### Post by jstad on 2006-12-13
> **Turbojoe said:**
> I had read about that procedure and tried it. However the drive is partitioned and it said it COULD possibly make all partitions unreadable. That scared me off and I aborted. I don't want to lose the info on the other partitions. Am I being overly concerned? 
Thanks,

Joe

Yes your system will be fine. It is just writing a new MBR and windows does the "disclamer" to protect from the "well we warned you" side of things.

---

### Post by Stew2 on 2006-12-13
> **Turbojoe said:**
> I had read about that procedure and tried it. However the drive is partitioned and it said it COULD possibly make all partitions unreadable. That scared me off and I aborted. I don't want to lose the info on the other partitions. Am I being overly concerned? 
Thanks,

Joe


If you have valuable or hard to replace data on your hard drive I would error on the side of caution and back it up first. I have rewritten my MBR with the XP disk numerous times and never had a problem but it is better to be safe than sorry! :D 

Regards,
Stew2

---

### Post by Turbojoe on 2006-12-13
Thanks guys. Hopefully I'll get time to try it tomorrow. 3:00 a.m. comes early so I'm heading to bed now. 

I have a 900mhz system thats not being used now. All it needs is a hard drive. Maybe I'll pick up a cheapo for it and set it up with Ubuntu. I liked what I saw in the very short time I played with it. I think it'll be worth learning when I get the time I need to devote to it.

Thanks,

Joe

---

### Post by Turbojoe on 2006-12-14
Thank you gentlemen. fixmbr worked fine with no data loss! Now I need to format the drive and ship it out to my daughter.


Joe

---

### Post by Fully216 on 2006-12-15
Glad to hear that it went well.  Also good to know we could help.  Let us know if there is anything else we can do.  ;)

---

### Post by Turbojoe on 2006-12-15
Seems to be lots of good people here. I'll be back soon when I have more time to devote to learning Ubuntu.

Thanks again to all that helped me out.

Joe

---

