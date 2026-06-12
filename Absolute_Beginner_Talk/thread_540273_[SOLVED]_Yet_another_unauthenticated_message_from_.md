---
title: "[SOLVED] Yet another unauthenticated message from synaptic"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by apunc1 on 2007-09-01
I have Just done a clean install of Feisty on my desktop and when I tried to install the system updates after the reboot i received the "Updates are not Authenticated" message. I see that has happened to many people in the past few months.
When I try to do a sudo apt-get update I get this message: E: could not get lock /var/lib/apt/lists/lock - open (11 resources temporarily unavailable)
E: unable to lock the list directory.

Any thoughts?

---

### Post by mocoloco on 2007-09-01
When I get that error message I just hit reload in synaptic, and then it clears up.  Seems like it happens because it doesn't finish downloading the repository info.

---

### Post by apunc1 on 2007-09-01
> **mocoloco said:**
> When I get that error message I just hit reload in synaptic, and then it clears up.  Seems like it happens because it doesn't finish downloading the repository info.

I did that and it gave me the same message it gave me in the terminal, about unable to unlock the list directory.

Is this a server problem? I installed feisty on a spare desktop last month with this exact install cd and everything was fine.

---

### Post by mocoloco on 2007-09-01
Don't know if you've tried this, look at the last two posts on this page: [http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem]("http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem")

Just goolging for that error message, it does appear to only be happening on servers.  Strange.

---

### Post by apunc1 on 2007-09-01
> **mocoloco said:**
> Don't know if you've tried this, look at the last two posts on this page: [http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem]("http://www.ubuntux.org/synaptic-sudden-reboot-exclusive-lock-problem")

Just goolging for that error message, it does appear to only be happening on servers.  Strange.

mocoloco, thanks for your replies. 
When I said server, I meant the Ubuntu update server. 
I am currently doing  a fresh install  of dapper. It went fairly quickly because i had my partition sizes set from the initial feisty attempt.
I think this machine has a problem with feisty in general, maybe some odd hardware thing. I haven't done any in depth research, as I for this machine I just want a stable system for internet surfing and multimedia storage and viewing. 

The package updates for Dapper just now did not give me this error.

---

### Post by robotii on 2007-09-01
Have you got auto download enabled? I have found that if you have this turned on in software updates, it can sometimes cause this problem.

---

### Post by dptxp on 2007-09-01
Open Add/Remove
Click on "preferences" at bottom left.
Choose best server and let Ubuntu locate it.
Save and close.

---

### Post by apunc1 on 2007-09-01
dptxp and robotii thanks for your replies. I will try your tips once I get feisty installed. yes, i'm installing feisty again because while dapper installed fine, i was having dependency issues installing the mozilla build of firefox and could not get it installed no matter what dependencies i installed.
It's odd that I am having problems installing ubuntu because when I installed it a couple of years ago for the first time, my install was trouble free. maybe it's time to try a new distro :confused: it's probably user error (a.k.a. me)
i'll try with feisty once more and post back my results.

---

### Post by apunc1 on 2007-09-01
the updates worked this time without the not authenticated message

thanks all for the tips.

---

