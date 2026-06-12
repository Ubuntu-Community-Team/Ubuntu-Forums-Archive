---
title: "How do I enable a system user after adduser?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by mrbig1492 on 2008-02-28
Hello,
I added a system user with adduser and gave it a password with passwd.  When I try logging on with that user id and password I get "user has been disabled by administrator" or something like that.  What else do I need to do for this user to work?

Thanks,
Ernie

---

### Post by SOULRiDER on 2008-02-28
Try unlocking it with the -U option.
```
sudo usermod -U <user>
```

---

### Post by mrbig1492 on 2008-02-28
Thanks for the reply.  I tried it and the result is still the same.  I get the dialog box with the "stop" symblol icon and the message, "The system administrator has disabled your account"

---

