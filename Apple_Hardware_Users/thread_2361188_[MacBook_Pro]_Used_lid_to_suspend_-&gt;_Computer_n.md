---
title: "[MacBook Pro] Used lid to suspend -&gt; Computer no longer stays suspended with lid open"
date: 2017-05-13
forum: Apple Hardware Users
---

### Post by &amp;KyT$0P# on 2017-05-13
Title pretty much says it all.  I'm running Xubuntu 16.04.  This behavior did not occur in Lubuntu 14.04.

I had this issue once before, and it seemed to go back to normal after I had to force-poweroff my system and run fsck from a live USB.  But I'm not inclined to do that every time I use the lid to suspend. :P

For now I'm using the workaround of disabling the LID0 wakeup device when this occurs.  But I don't consider that a solution either, because I would like to be able to use the lid to suspend and wake.

How to fix this?

---

### Post by MikeBraxner on 2017-05-13
Have a look at [*(2) Instant Resume from Suspend*]("https://ubuntuforums.org/showthread.php?t=2299760&p=13377327#post13377327") ... *(wake-ups from LID0 need to be suppressed as well,  ideally in such a way  that suspend via lid-close/wake-up on lid-open still works properly)* ... this should be what your looking for, just follow the indicated links.

---

### Post by &amp;KyT$0P# on 2017-05-13
That did the trick.  Thanks MikeBraxner! :KS

---

