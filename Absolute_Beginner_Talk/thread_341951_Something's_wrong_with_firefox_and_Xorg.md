---
title: "Something's wrong with firefox and Xorg"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by korla on 2007-01-19
I'm new to ubuntu, but I do have some experience with Linux (switched to kubuntu from debian recently). Overall I love my kubuntu (6.06), but I just ran into an odd problem. This is what it looks like:
I have 2 user accounts and one has more privileges than the other. The idea was to have an account where I can have someone login and browse the net and such, but not be capable of SUDOing my system to death.
Now, when I run firefox (that I got off synaptic, Firefox. 1.5.0.9) on the less privileged account very quickly the computer becomes extremely slow. I looked at top and it tells me that Xorg is hogging all the memory (it was 400Mb and growing when I looked at it, compared to about 60-80Mb on the account where everything work fine).
Same thing happened when I tried running eclipse from that not so privileged account.

Any ideas on why is this happeneing and more importantly how to fix this? ](*,)

---

### Post by Ecthelion on 2007-01-19
Not immediately an answer to your problem, but what do you mean with:

> The idea was to have an account where I can have someone login and browse the net and such, but not be capable of SUDOing my system to death.

Except if you tell anyone your password, they can't. Without your password they can't "sudo" a thing...

> Same thing happened when I tried running eclipse from that not so privileged account. 
Eclipse always sucks a lot of memory...

> Any ideas on why is this happeneing and more importantly how to fix this?
You could check the logs to look for a reason...
If you use edgy then it's just System > Administration > System log

---

