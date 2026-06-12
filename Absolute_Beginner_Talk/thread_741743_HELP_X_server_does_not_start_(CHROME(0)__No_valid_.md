---
title: "HELP X server does not start (CHROME(0) : No valid modes found)"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by jubilee0824 on 2008-04-01
Hi

I updated to 8.10, working fine for few days, then suddenly ubuntu does not boot up anymore. I went to the recovery mode, and found that xserver was a problem.

When I type sudo startx, I get the following error
(EE) CHROME(0): No valid modes found
(EE) Screen(s) found, but none have a usable configuration.

I tried dpkg-reconfigure, apt-get install--reinstall xserver-xorg-core,,,,neither worked and I don't know what more to do.

please help if anyone knows a solution!
thanks.

---

### Post by mikeyphi on 2008-04-01
You should ask in the Hardy Forum - I think you'll find that Chrome is a problem.
However the correct code to try is:

sudo dpkg-reconfigure -phigh xserver-xorg

answer the questions as best you can!

---

### Post by igknighted on 2008-04-01
It's beta for a reason, these things happen.  Check launchpad and make sure a bug has been filed and look for solutions, as well as the hardy development forum here.

---

