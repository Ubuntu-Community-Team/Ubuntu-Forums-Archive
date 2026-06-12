---
title: "Xunbutu 7.10 fails at hardware driver loading."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by synking on 2008-01-18
I have installed xubuntu on an old compaq armada P2 128 mb of memory.  Everything installed fine and it was able to boot several times without and hang up's or issues.

But now when it loads it stalls at loading hardware drivers for sometime then gives me the fail and continues to load but does not complete.

It stalls at different times sometimes as soon as the fail to hardware sometimes 4 or 5 steps after..

Is there a command that i can call that will show me where it is actually stopping..

I know that this was a problem with older versions but i can't seem to get any of those steps to work.

---

### Post by gn2 on 2008-01-18
For a P2 with 128mb RAM I would recommend a switch to Zenwalk.
7.10 seems to need higher system specs than 7.04 in my experience.

[www.zenwalk.org](www.zenwalk.org)

---

### Post by JoshuaRL on 2008-01-18
Have you tried booting into the recovery console?  It might tell you a little more about what is failing.

---

### Post by spiderbatdad on 2008-01-18
i believe you can edit the boot line when grub loads...hit f6, then delete the end of the line where it says "quiet splash"  If you hit f1 you can browse other parameter options you may need to add vga=771. I think I did this once on the same machine...deleting everything back to and including "ro" then added "noapic nolapic vga=771"  no quotes. 128 mb should be fine for xubutu.

---

### Post by bwhite82 on 2008-01-18
> Is there a command that i can call that will show me where it is actually stopping..

Yes, but only if you can successfully boot into "safe mode". If so, from the command line simply enter:

> dmesg

Or to save it as a file:

> dmesg > boot.txt

dmesg outputs your boot log and will show you whats going wrong where.

-Cheers

---

### Post by synking on 2008-01-18
Thanks for the options i will have to try that one..... i have attempted to run the recover a broken system that is built on the cd but it never starts

---

### Post by synking on 2008-01-19
Ok so having it load in text mode seemed to fix the boot problem 3 boots and no problem and can't find any where that it failed with dmesg i think it maybe the display driver but i forget how to start the GUI from terminal. any help on that guys.

---

### Post by JoshuaRL on 2008-01-19
```

startx

```

Try that, it will launch Xserver and your GUI of choice (Gnome, KDE, XFCE, Flux).

---

### Post by synking on 2008-01-19
thanks guy seemed to have fixed all my worrys for now...

thanks for all the help

---

