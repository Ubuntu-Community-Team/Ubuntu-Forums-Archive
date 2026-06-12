---
title: "Installing the Dohickey Project Client."
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by quinnten83 on 2008-01-10
I just installed the Dohickey Project client from their webpage (version alpha 6.02), but nothing happens and it keeps saying, waiting for servers.
I tried manually inserting a server, but I can't find the address of a server anywhere.
Could anybody tell me what it is that I am supposed to be doing?
The previous posts didn't offer a solution to this problem.
I really like the idea of this project.

---

### Post by DoctorMO on 2008-01-13
There is probably more errors happening; but since we've been working on Dohickey 0.7 (I'm the lead programmer btw) the bugs are most likely fixed. there is just rather a lot to do at the moment since there is a full server side as well as the client side to code.

you have the option of waiting for the next release or installing from cvs if your confident enough; instructions are on our download page.

---

### Post by quinnten83 on 2008-01-13
I will wait, cause I definitely am not confident enough yet.
But thanks for getting back to me,I really appreciate it.

---

### Post by DoctorMO on 2008-01-13
One of our testers does have this nightly build if you want to install it, it's very new so let me know if you experience any problems. I'd also change the server to parsed.net as that is where we have the test server running.

[http://parsed.net/~orion/tmp/dohickey_0.7_all.deb](http://parsed.net/~orion/tmp/dohickey_0.7_all.deb)

---

### Post by quinnten83 on 2008-01-16
Will installing the .deb automatically remove the previous version or replace the necesarry files?

---

### Post by DoctorMO on 2008-01-16
No, it will overwrite many files though; you best bet is to remove dohickey using dpkg remove. Although it'll still work even if you don't.

---

