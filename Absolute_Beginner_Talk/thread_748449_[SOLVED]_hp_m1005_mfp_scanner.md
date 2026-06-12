---
title: "[SOLVED] hp m1005 mfp scanner"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Peter_H on 2008-04-07
Hi,

Please help me, if somebody has the answer: how to use hp m1005 mfp scanner in ubuntu.

Thank you.

Best regards,
Peter H

John 13:34

---

### Post by linuxwizard on 2008-04-07
According to this it is supported > [http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

Have you installed Sane ?
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

[http://tldp.org/HOWTO/Scanner-HOWTO/index.html](http://tldp.org/HOWTO/Scanner-HOWTO/index.html)

---

### Post by Peter_H on 2008-04-07
Thank you very much for the answer.

Sane is installed

scanimage -L gives the following answer:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


do I need hpljm1005 backend?
where I find it?

Peter H

---

### Post by Peter_H on 2008-04-10
Thank you, linuxwizard, you helped me understand it.
The hpljm1005 backend is included in the latest sane version.

The scanner does not work in ubuntu gutsy, which has an older sane on the repositories.
But it works very well in ubuntu hardy. :)

---

### Post by linuxwizard on 2008-04-10
Sorry I didn't reply to your question on hpljm1005 backend. I didn't notice that you posted another question the other day.. Having alot of trouble getting around on the forum to slow & timing out. Not spending as much time here. But it sounds like you got it figured out and your scanner is working which is great. Good Luck
Please mark thread as SOLVED.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

