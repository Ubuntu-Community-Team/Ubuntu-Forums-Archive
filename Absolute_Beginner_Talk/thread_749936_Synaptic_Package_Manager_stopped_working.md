---
title: "Synaptic Package Manager stopped working"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Amish_Gramish on 2008-04-09
I don't know what I did, but whenever I try to go into Synaptic Package Manager, it always says:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
E: _cache->open() failed, please report.

I'm relatively new with Linux, but I've been able to follow these (great) "walkthroughs" on these forums, and the help of an acquaintance of mine, but I can't find anywhere how to fix this.

---

### Post by InfinityCircuit on 2008-04-09
go to Applications -> Accessories -> Terminal and type "sudo dpkg --configure -a".  It will ask you to type in your password.  Do this, wait for it to finish, and then you should be set.

---

### Post by Amish_Gramish on 2008-04-09
> **InfinityCircuit said:**
> go to Applications -> Accessories -> Terminal and type "sudo dpkg --configure -a".  It will ask you to type in your password.  Do this, wait for it to finish, and then you should be set.

Thanks!
Now back to Statistics... ](*,)

---

