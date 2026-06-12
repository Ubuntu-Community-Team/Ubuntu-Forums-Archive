---
title: "Hard freeze with current kernel"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Henry Rayker on 2007-02-25
I updated to the 2.6.7-11 kernel a little while back. So, a little while afterward, my laptop hard freezes. Nothing can bring it out of the freeze aside from holding the power button until it shuts down. The wifi seems unresponsive (although the Link LED is still lit...I'll see if the other machines on the network can see it the next time I get this error). The mouse has no response, nor does the keyboard (I can't even CTRL-ALT-F1 for tty1 etc). I should point out that, in the previous kernel (2.6.7-11) it works without problem; no freezing etc.

Are there any logs for me to check to try to figure out what is going wrong?

Thanks

---

### Post by n8bounds on 2007-02-25
look at the files in /var/log/
(messages, syslog, etc...)

Maybe switch to the 386 kernel..

---

