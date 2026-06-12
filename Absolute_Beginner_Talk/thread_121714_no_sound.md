---
title: "no sound"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by mbmack on 2006-01-25
my sound isnt working and was wondering about a few things i could try.  I know it might not ever work but i would at least like to try.  I have an old laptop, compaq presario 1626.  I looked in the divice manager and i think it is there.

---

### Post by mbmack on 2006-01-25
can someone at least point me in the right direction?

---

### Post by Razorback on 2006-01-25
I had the same problem.  I got mine working by System => Preferences =>Multimedia System Selector then changed Audio output to ALSA.  It was on OSS and would not work.  HTH

---

### Post by mbmack on 2006-01-25
Thanks for the reply but I had already tried that and it said "failed to construct test pipeline for ALSA..." when i clicked on test.

---

### Post by Razorback on 2006-01-26
Does you device manager give any information about your onboard sound?  If you can find it, you can go to the Alsa webpage and see if there is support for it.  Your laptop appears to have an Aureal sound chip.  If so, check out this link:

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Aureal](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Aureal)

---

