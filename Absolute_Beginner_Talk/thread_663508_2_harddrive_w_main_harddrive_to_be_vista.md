---
title: "2 harddrive w/ main harddrive to be vista"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by clark0820 on 2008-01-10
Hello all,

       I currently have a laptop that have vista on the 1st harddrive, then I install XP and ubuntu on the 2nd harddrive. After that I decided I don't really wanna have the 2nd harddrive on my laptop, however, when I unplug the 2nd harddrive, grub will give me "error 21". I can only start my laptop with my 2nd harddrive plug in. I wonder how can I erase grub, so that my laptop can start by only the 1st harddrive w/ only vista on it. Thanks a lot.

Clark

---

### Post by ByteJuggler on 2008-01-10
Disconnect the second drive, boot with your Vista CD, and perform a "startup repair".  If that doesn't work, boot up as before, open a command prompt, and enter in there:

```
bootrec /fixmbr
```

You will then have to boot your other OS's using for example the "Super GRUB" disk, however, as your compuer will then only boot Vista by default, from its primary hard drive.

---

