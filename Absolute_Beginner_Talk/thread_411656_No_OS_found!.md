---
title: "No OS found!"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Spectre5 on 2007-04-17
Ok....now what...

I have random computer freezes/lock-ups/whatever you want to call them...

I removed powernowd (this is a desktop, powernowd does nothing for my cpu anyways), then I had a computer freeze shortly thereafter.....now I can't even boot into linux!!!!!!!

When I restart I get a message saying that no OS was found on the system!

AHHH!

Any ideas?

---

### Post by aberry5555 on 2007-04-17
If it says there's no OS it means it's not reading your hard-drive. This either means that your hard-drive is entirely corrupt, which is quite hard to fix, but **_might[B]**_[/B] be possible, or it means that your hard-drive has failed which, due to the random freezing seems more likely.... If the hard-drive has failed you will need to buy a new one and to recover the data it would have to be sent off to professionals. An easy way to check if it's failed is to put the live-cd in again, load it, open a terminal and type in 

```
sudo fdisk -l
```

(the -l being an L in lower-case)

and post the results back here.

Good luck

---

### Post by Spectre5 on 2007-04-17
Weird....I looked at the bios and it appeared that the computer did not detect the hard drive...so I opened up the case, unplugged the power and IDE cables, plugged them back in...then viola and it worked....

I don't know how this happened by a simple restart...my computer is far enough away from me that I couldn't kick it...I have no idea how it may have come loose....but oh well...all is ok again (besides the random restarts...someday I'll find my answer...someday)

Thanks

---

### Post by aberry5555 on 2007-04-17
np, sounds like a dodgy power-supply rather than the IDE cable.

---

