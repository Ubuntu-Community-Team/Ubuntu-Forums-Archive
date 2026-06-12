---
title: "FDSK won't work; cannot boot up anymore"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by carpola on 2007-04-13
So when I go to boot my linux partition, I get a message saying the drive hasn't been mounted in a long time and that it needs to run fdsk, which it automatically does. however, as it completes it, it says that it fails, and that i will need to run it manually. it then exits out and goes to bash, where i have no idea what to do. what should i do now?

---

### Post by carpola on 2007-04-13
hasn't anyone even VIEWED this thread yet?

---

### Post by carpola on 2007-04-13
anyone, please? this is the only thread that hasn't had an actual reply from someone other than the OP. my linux won't even boot up! i need to run it again!

---

### Post by mrpooch03 on 2007-06-16
Had the same problem today..  I think it might be a partition issue, but what ever the reason, got the same message.  If I remember correctly, at the login prompt at the end of the message, I typed "fdsk"  It came back with a bunch of errors and asked me if I wanted to correct.  Not knowing exactly what I was doing, I answered "Y" to each question.  When fdsk was complete, I did CTRL/ALT/DEL.  Ubuntu did a normal shutdown.  I restarted and it ran back up good as new.  Hope this helps...

---

### Post by rdjurovich on 2007-09-30
> **mrpooch03 said:**
> Had the same problem today..  I think it might be a partition issue, but what ever the reason, got the same message.  If I remember correctly, at the login prompt at the end of the message, I typed "fdsk"  It came back with a bunch of errors and asked me if I wanted to correct.  Not knowing exactly what I was doing, I answered "Y" to each question.  When fdsk was complete, I did CTRL/ALT/DEL.  Ubuntu did a normal shutdown.  I restarted and it ran back up good as new.  Hope this helps...

Same thing happened to me just now after installing updates and rebooting, so I entered the root password and typed fdsk (then enter), asked me if i wanted to fix a few things (pressed y for yes of course!), then once everything was done ctrl-d and it rebooted fine :D

---

