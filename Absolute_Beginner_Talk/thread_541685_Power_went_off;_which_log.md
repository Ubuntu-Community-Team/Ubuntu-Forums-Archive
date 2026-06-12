---
title: "Power went off; which log?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by JengaBlocks on 2007-09-03
Earlier this week, my Xubuntu system lost power. I looked at my Xubuntu machine and noticed that it had rebooted. The Xubuntu CD was in the CD drive and the CD install menu was up.

Is there a log file that could assist that can give me a rough estimate of when it went down?

---

### Post by Ashfire908 on 2007-09-03
I'm not sure where it will show the point when the system began restarting, (maybe syslog or kernel? auth should show the command being run if shutdown was used because root is need to do that) but i know for sure that there will be something like this in kern.log:

[ 352532.453] System halted

That means the system at that point halted and rebooted. Unfortunetly, that line does not contain anything to tell you when the system halted (without doing a lot of work) look around that line on the kern.log (and i think kernel stuff comes up in syslog too, so look there). post if you find anything (but not the whole log!), and I'll/someone else finding this post will help you with it.

---

