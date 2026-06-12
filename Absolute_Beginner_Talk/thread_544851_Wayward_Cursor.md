---
title: "Wayward Cursor"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by mdrowe on 2007-09-06
My cursor wanders to the upper right corner of the screen and stays there.  Sometimes it wanders slowly, sometimes it streaks, but every time it remains there.  Touch pad and two other mice produce similar, but not identical results.  Is this a software problem in Ubuntu 7.04?  What fix?

---

### Post by BrendanM on 2007-09-07
I had a similar issue on my Dell laptop. I'm still not entirely sure if it's hardware- or software-related. You should start by looking at your xorg.conf. If there's any sections in there about a "wacom" tablet-PC, you should comment them out. That helped some for me, but didn't fix everything.

Here's my own thread, I'm not sure how much help it will be to you. [http://ubuntuforums.org/showthread.php?t=321508](http://ubuntuforums.org/showthread.php?t=321508)

---

