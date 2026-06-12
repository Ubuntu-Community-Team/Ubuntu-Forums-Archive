---
title: "Can't boot 8.04 on ibook"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by gumara on 2008-04-25
I've install ubuntu ppc by alternate cd. but I get blank black screen. (Loade yaboot and next I see 2 line then get blank screen)

info
- iBook g4 12" 1.2GHz
- 8.04 alternate Stable release (checked md5sum)

---

### Post by lordfly on 2008-04-25
> **gumara said:**
> I've install ubuntu ppc by alternate cd. but I get blank black screen. (Loade yaboot and next I see 2 line then get blank screen)

info
- iBook g4 12" 1.2GHz
- 8.04 alternate Stable release (checked md5sum)

Same here. Black screen on a g3 dual usb

---

### Post by stream303 on 2008-04-26
Have you tried using the radeon framebuffer at the second stage boot: prompt?  (just hit -tab- when you see it come up so you can delay the timeout and type your kernel parameters in:)

```
Linux nosplash video=radeonfb
```

There are a few good threads about ati startup kernel parameters in the ppc archives, but with Hardy, it might be a whole new ballgame. :)

Anything in these two faqs that might help - again with the note that they may not work or be applicable to Hardy, but I guess we'll find out. :)

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

