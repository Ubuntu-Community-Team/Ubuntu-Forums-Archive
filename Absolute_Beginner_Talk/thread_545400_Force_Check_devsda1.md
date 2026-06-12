---
title: "Force Check /dev/sda1"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by FFRQ on 2007-09-07
So lately I've had issues with a frozen screen. The screen would stop but the cursor wouldn't and eventually all would be well. I recently restarted it and now when it boots up it says that /dev/sda1 had been mounted 26 times without a check and a forced check starts. This wasn't a problem at first, but has become one since the check never finishes. It will normally get to 22.2%, 25.6% or 25.2% 
It's never gotten as further than 78.2%. Is there a way to un-force the check or at least ensure that it finishes?

I've tried booting on both my kernels, but to no avail.

Q

---

### Post by P235 on 2007-09-07
Hi Q, your frozen screen problem does not sound like a good thing.  Have you run memtest a few times to check if your RAM is functioning properly?  Usually the fsck program runs to patch things up from nasty crashes or freezes.  If you would like to configure the auto-check, read this post:

[http://ubuntuforums.org/showpost.php?p=2116779&postcount=3](http://ubuntuforums.org/showpost.php?p=2116779&postcount=3)

---

### Post by tyggna1 on 2007-09-07
Well, you could try pressing ctrl-alt-F1 to get to the command prompt, from there, the command to disable the check would involve a program named
```
tune2fs
```

type in
```
man tune2fs
```
for exact usage instructions.


exact command to turn it off is:
> sudo tune2fs -c 0 /dev/sda2

but that's not advisable.

---

### Post by FFRQ on 2007-09-07
So is there anything that is advisable?

Q

---

### Post by philinux on 2007-09-07
Get grub to boot into diagnostic mode.

then at the command prompt run fsck

---

