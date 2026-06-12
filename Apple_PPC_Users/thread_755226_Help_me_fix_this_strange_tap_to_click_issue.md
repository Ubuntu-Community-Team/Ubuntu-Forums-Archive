---
title: "Help me fix this strange tap to click issue"
date: 2008-04-14
forum: Apple PPC Users
---

### Post by ndlsjk on 2008-04-14
Hey guys,

I have a problem with my touchpad on my iBook G3 800MHz on 8.04.

The tap-to-click feature will not work after I boot the system and log in, It also will not work if I log out and log back in, however, when I suspend the computer and wake it back up, I have a fully functioning tap to click touchpad.

What do I need to do to make this work all the time?



Thanks,
Jake

---

### Post by stream303 on 2008-04-14
> **ndlsjk said:**
> What do I need to do to make this work all the time?

Ah, check this out:
[https://wiki.ubuntu.com/PowerPCFAQ#head-341b2526a7463780f67059c7bc7ec0a4635f2eab](https://wiki.ubuntu.com/PowerPCFAQ#head-341b2526a7463780f67059c7bc7ec0a4635f2eab)

Even though you can't control it initially, the mere fact that it does at some point is good news.  Previously the only way I could control it was to type this in manually at every boot.  Look forward to the devs getting this to be automatic!

---

### Post by swash_buckle on 2008-04-15
I'm brand new to this here Linux world, but I think I might have an answer for you.

Pardon my non-forum-savvy instruction.  In Terminal:

sudo nano /etc/pbbuttonsd.conf

Now scrolll down to the bottom of the list and you should find:

TPMode = notap

Edit this line to either TPMode = tap or TPMode = drag

Now (control + x) to exit, you should be prompted to save.  Probably a good idea.

This worked for my iBook G4.  Hope this works for you and good luck.

---

### Post by ndlsjk on 2008-04-15
stream303 - That worked! Is there anyway to create a script to do that at boot automatically? I didn't see anything in the wiki, but maybe we could figure it out!

swash - I tried both tap and drag, and neither worked. I saved the file of course and did a full logout/login and I still didn't have the tap feature. Maybe that only works on the G4s or maybe my laptop is a freak....it has been thrown onto a hard floor more than once :)

Thanks a million guys,
    Jake

---

