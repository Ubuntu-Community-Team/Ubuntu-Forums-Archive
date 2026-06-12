---
title: "Newbie to Ubuntu, some questions. [Resolved]"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by stchman on 2007-02-11
I have installed Ubuntu 6.10 and really like it.

I have a few questions about it.

How do you get to root in a terminal?  In other linux distros it is "su" then the password?

Next question:

This machine is dual boot WinXP and Ubuntu.  How do I get to the other HDs?

Thanks

---

### Post by aysiu on 2007-02-11
You don't get to a root terminal. If you must, though, just type ```
sudo -i
``` More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Mounting Windows partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by rabid emu on 2007-02-11
In Ubuntu use 'sudo' whenever possible.

---

### Post by stchman on 2007-02-12
> **aysiu said:**
> You don't get to a root terminal. If you must, though, just type ```
sudo -i
``` More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Mounting Windows partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Excellent, sudo -i asked me to enter a password and viola it worked just fine.

Thanks guys.

---

