---
title: "Can't create folders in some directories"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-15
Is there a reason that I can't create new folders in directories other than my Home folder in Ubuntu 7.10?  I have administrative privileges with the account I am logged in under.  Thanks.

---

### Post by celticbhoy on 2008-01-15
You would need to be root to make a folder outside your home directory. Why do you want to do this.

---

### Post by bodhi.zazen on 2008-01-15
yes it is by design

You need to exercise your admin rights with sudo

[uwiki]RootSudo[/uwiki]

You may also want to look at permissions on Linux

---

### Post by Matt26 on 2008-01-15
Thanks for the responses- just a curiosity really- I'm new to Ubuntu (and refreshing my experience with Linux in general).  Thanks.

---

### Post by nikoPSK on 2008-01-15
you can sudo mkdir in places in which root access ir required, or chown the folder. :)

---

