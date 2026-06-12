---
title: "Dell 1390 wifi card installation help"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-09
I have a dell latitude D620, and I have tried installing ndiswrapper 1.48, checking the laptop page, and using the windows wireless driver tool, and i cannot get my wifi card to work. please help me!

When I try to install ndiswrapper, I get

$ tar -zxvf ndiswrapper-1.48-tar.gz
tar: ndiswrapper-1.48-tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by strabes on 2007-10-09
Where did you download the ndiswrapper file to? You're most likely not in that directory. To get there, run:```
cd /path/to/location/ofthefile
```Then run the original tar command.

---

### Post by iamthemicrowave on 2007-10-09
ok I fixed that, now it is installed, i would assume.
When i run

$sudo ndiswrapper -l

i get

bcmwl5 : invalid driver!

what does this mean

---

