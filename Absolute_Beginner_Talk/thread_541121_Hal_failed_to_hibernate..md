---
title: "Hal failed to hibernate."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-09-02
When I click the hibernate button I get the following error message:

HAL failed to hibernate

I know this has been brought up time and time again, and I apologise but I believe my problem is slightly different to that of others.

At first when I tried to use the hibernate option my computer just froze up and when I could see the mouse it was stuck at a point on the screen and my screen was black.

Then I did a bit of research and I found this solution: [http://ubuntuforums.org/showthread.php?t=471855&highlight=hibernate](http://ubuntuforums.org/showthread.php?t=471855&highlight=hibernate)

at the time when I did the: sudo s2ram (to suspend), it put the laptop to sleep and I could resume and continue using without a problem. Now I get this error:

> 

Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Hewlett-Packard"
    sys_product  = "HP Pavilion dv5000 (RF999EA#ABV)  "
    sys_version  = "F.17"
    bios_version = "F.17"
See [http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram) for details.

If you report a problem, please include the complete output above.


Also, when I did the --force option the computer just freezes up on resume (with black screen).

Doing sudo s2disk (hibernate) gives the following error: 
> 

suspend: Could not use the resume device (try swapon -a)


Before it worked fine.

Finally, I changed the two HAL files as recommended in the post.

So at first everything was fine, I tested it a few times (by pressing the shutdown button, and then clicking hibernate and sleep). Then I restarted the computer and I've been getting these errors, and when I try to sleep and hibernate using the shutdown button, my computer goes into the lock screen mode asking for my password to unlock, and upon unlocking I get the Hal failed to initialize error.

Any thoughts?

---

### Post by abhiroopb on 2007-09-10
Any thoughts?

---

### Post by silent1643 on 2007-09-10
i didn't really read your post in detail (to lazy) but you could try re installing hal components from synaptic

---

### Post by abhiroopb on 2007-09-19
what is hal exactly?

---

