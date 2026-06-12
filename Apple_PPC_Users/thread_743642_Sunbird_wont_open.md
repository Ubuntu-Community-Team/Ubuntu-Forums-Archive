---
title: "Sunbird wont open"
date: 2008-04-02
forum: Apple PPC Users
---

### Post by atok on 2008-04-02
hi,

i installed sunbird from repository (using apt-get). it installed fine and smooth. but when i run it, only the outer frame and part of calendar is visible. and i have no control over it. i've tried to let it run for a while hoping that it is just my ibook is too slow. but still no change. i've search this forum and found some suggestion, i've tried all but still doesn't work.

---

### Post by BladeMelbourne on 2008-04-02
Can you start Sunbird from a terminal/console window and report back if any error messages were output to the terminal window?

It almost sounds like a required library is missing (which you would think would have been handled by apt).

---

### Post by stream303 on 2008-04-03
Ah, my favorite cross-platform calendar!  I really like it, although the calendars in Evolution come close.

Like BladeMelbourne, I also wonder if there is a missing library.  I know that when I download it directly from the site, I must make sure that I have libstdc++5 installed.  Ya' know here on Gutsy it is still at 0.5, and I like the latest 0.7 that shows up in Hardy Beta.  If 0.7 doesn't show up in the backports, maybe I'll download it manually for my Gutsy box.

Anyway, is there any way you can grab a window resize handle somewhere and try to drag it down to a reasonable size?  I think I remember having the same issue until I manually resized it and bingo.

---

