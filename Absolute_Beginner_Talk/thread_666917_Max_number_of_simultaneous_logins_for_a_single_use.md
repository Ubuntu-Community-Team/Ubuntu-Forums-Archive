---
title: "Max number of simultaneous logins for a single user"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by tieflingrogue on 2008-01-13
Just wondering, how many times can the same user login to linux from different terminals or windows at the same time.  On my system, I was able to login to all 7 virtual terminals and do su myusername a few times.  The who command showed that I was logged on 13 times.  Is there a preset limit to this, or can you just keep logging in?

---

### Post by naugiedoggie on 2008-01-13
> **tieflingrogue said:**
> Just wondering, how many times can the same user login to linux from different terminals or windows at the same time.  On my system, I was able to login to all 7 virtual terminals and do su myusername a few times.  The who command showed that I was logged on 13 times.  Is there a preset limit to this, or can you just keep logging in?

Hello,

/etc/security/limits.conf contains the option to limit logins for users.  The file is well-commented.

I don't believe there is any default limit, beyond resources.  For remote logins, I believe there is a limit to the number of getty processes that can be spawned to "answer the phone," but I'm not aware of its value.

Thanks.

mp

---

