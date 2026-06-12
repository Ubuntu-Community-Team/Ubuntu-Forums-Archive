---
title: "GRUB loader breaking my Windows XP and Ubuntu partitions"
date: 2008-02-03
forum: Apple Intel Users
---

### Post by cksubs on 2008-02-03
I'm currently triple booting my MBP with Leopard, XP, and Ubuntu. I redid my whole partition scheme about the time leopard came out, installing Leopard on one, XP on another, and leaving the Linux one blank for a while. This worked fine for more than a month. I then installed Ubuntu on the last partition, and it worked fine for about a week. I hardly used Linux at all during that time.

Then, after rebooting from OS X into XP, I get this error:

"[ Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]"

and Windows refuses to boot. I try Ubuntu, it won't boot as well, same error. I came here, did a search, and found someone with a similar problem. He was putting a lot of work into it, and it didn't seem like he was getting anywhere. So instead of trying to fix it I just reformatted the Linux partition. I still got the GRUB error trying to load Windows after this, but after reinstalling Ubuntu it went away.

I've done this three times now, and I'm getting sick of it. The last time, I only got through one reboot of Windows until it broke on me again. HOW do I fix it? I'm getting to the point where I'm sick of trying to fix Ubuntu and would be fine with just OS X and XP, but it seems as if I can no longer boot XP without Ubuntu on the system. Any help would be great, I'd really like to get all three systems working.

---

### Post by cyberdork33 on 2008-02-03
it sounds like something is breaking Grub. check the link in my signature about how to multi boot properly. You will not have to rely on grub to boot XP.

---

### Post by cksubs on 2008-05-05
What the HELL is wrong with this thing? This same damn "minimal bash like shell" error has been hounding me over three F-ing versions of Ubuntu, and I've never even gotten to use the damn OS because as soon as I finally get my wireless or my graphics card running (already annoying tasks themselves) the whole thing shuts down on me and I have to reinstall.

I just installed HH, and this time I was very careful to follow that guide above, click on "advanced" and set the GRUB disk to my /, etc. Today both Linux and Windows break again, both giving that same error. What can I do to fix this? Do I even need to use grub if I'm using rEFIt? Why would it even touch my Windows partition?

---

