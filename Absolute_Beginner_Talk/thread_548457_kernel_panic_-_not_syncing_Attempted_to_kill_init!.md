---
title: "kernel panic - not syncing: Attempted to kill init!"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2007-09-11
Yes, topic has been raised before, though it seems very unclear to me. 

I've been running Ubuntu for almost a year now and I've encountered many problems, and resolved them just by taking a quick look here at the forums. Now I got a new one!

It started back when my computer froze and told me it died with an **exit status 4**. I got some help telling me that I had to to a **fsck -v** to fix it, which it did. Today it happened again, it froze and I did a **fsck -v**, which fixed it, but also messed up my evolution, xmms, and gaim. 

Then my computer froze yet again, only this time it was because of gaim. My MSN contacts couldn't be synced with gaim, and I had to wait until 119 bars appeared telling me if I either wanted to add them to a seperate contact list, or not. Unfortunately I opened firefox at the same time, which made it freeze. I pushed the reset button and waited for it to boot, which it didn't.

I tried to solve it yet again with a **fsck -v**, but it didn't do the trick. I tried only **fsck** and didn't care about the warning message I was given. Then I got the final warning message which is this one:

[B]Begin: Running /scripts/init-bottom ...
Done.
run-init: /sbin/init: Not a directory
[      5.191801] Kernel Panic - not syncing - Attempted to kill init!
[      5.191846][/B]

Been looking about for someone with the same problems, haven't found any specific answers, only that either the RAM, HDD or DVD is broken, or misplaced. Can't be though, I've been up and running for almost a year!

Thanks in advance

Urk

---

### Post by urk_nono on 2007-09-12
Bump!

Seems like I have to take a backup of my home and reinstall Feisty Fawn :(

---

### Post by asmoore82 on 2007-09-12
i can't find a question in the post.
test the RAM with **memtest86** and test the HDD with **badblocks**

---

