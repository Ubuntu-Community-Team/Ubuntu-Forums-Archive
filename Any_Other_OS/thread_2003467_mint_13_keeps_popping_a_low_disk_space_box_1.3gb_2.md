---
title: "mint 13 keeps popping a low disk space box 1.3gb? 23gb really free!"
date: 2012-06-14
forum: Any Other OS
---

### Post by slixz85 on 2012-06-14
hi. i am not sure why linux mint 13 maya mate edition keeps popping this box up but it is the low disk space one with only the ignore button. I just installed mint 13 and I ACTUALLY have 23gb free right now on this drive. the installation is / and there is no partition setup seperately in this install. so this is very wierd.

---

### Post by HarryTorry on 2012-06-14
Out of curiosity, is your drive by any chance 450-500Gb in size?

---

### Post by slixz85 on 2012-06-14
> **HarryTorry said:**
> Out of curiosity, is your drive by any chance 450-500Gb in size?

no it is only a 250GB split into three partitions ext4 each partition is of about 50GB-60GB but each one as well actually has 25GB AT least of free space as the file manager tells me. plus cleaner installs on all 3. this is only os that has gave me this warning. I hope to keep linux mint 13. what exactly do you think could happen when it thinks it is out of space all the way?

---

### Post by HarryTorry on 2012-06-14
I remember seeing a thread similar to this a few days ago. The system keeps about 5% of the HDD (or boot partition, I think it's probably going to be the boot partition) so that it can safely boot! I'll try to find that thread now!

---

### Post by slixz85 on 2012-06-14
> **HarryTorry said:**
> I remember seeing a thread similar to this a few days ago. The system keeps about 5% of the HDD (or boot partition, I think it's probably going to be the boot partition) so that it can safely boot! I'll try to find that thread now!

ok thanks. hope i catch ya in time gotta go to work in hour or so. i will read later if not.

---

### Post by HarryTorry on 2012-06-14
Okay, well firstly there is [this]("https://answers.launchpad.net/ubuntu/+source/gnome-system-monitor/+question/8609")!
That explains the problem.

I can't actually find how to reduce this unfortunately. But be careful if you/somebody else knows, since it could potentially make your system not boot!

---

### Post by slixz85 on 2012-06-14
> **HarryTorry said:**
> Okay, well firstly there is [this]("https://answers.launchpad.net/ubuntu/+source/gnome-system-monitor/+question/8609")!
That explains the problem.

I can't actually find how to reduce this unfortunately. But be careful if you/somebody else knows, since it could potentially make your system not boot!

i just looked it over and it does sound similar i guess. i have to leave unfortunately real soon so i cant do it but i will check these post and run the tune program or whatever it was saying. thanks harry this could possibly be it but i am scared i could screw it up too so gotta research some more.

---

### Post by CharlesA on 2012-06-14
Check what this says:

```
df -ih
```

As for using tune2fs to change the amount of space for the root user, you can adjust it to 1% if you so desire, but I doubt it will have any effect on the missing 20GB.

---

