---
title: "Disk damage/password"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Cloudsoft on 2008-01-23
My hard drive was damaged in a Windows operation, I'm not sure how.
When I try to load Linux I get a message that one of the ext2 partitions must be repaired.  Then it asks for my root password.
It will not accept my password.
I've tried going to the install disk and running "sudo password root" from the terminal without success.
I've also tried running "e2fsck /dev/hda5" in the terminal without chaning the problem.
What else should I do?
Thanks

---

### Post by wormser on 2008-01-23
Nobody else seems to know so I will give you some thing to try.  Boot into the live CD and try to run the repair commands from there.

---

### Post by Cloudsoft on 2008-01-24
Thanks for the Idea, Wormser, but that doesn't work either.

I think I'll just have to re-format and re-install.

Thanks for the help though.

---

