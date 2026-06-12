---
title: "error message"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jocaasbe on 2007-09-18
I was downloading and installing updates.  I lost power in the middle of the operation.
When I resumed I got this error message.  I'm new to Ubuntu and Linux.  What do I do to make this happen?


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

Thanks,
jocaasbe

---

### Post by jamvegan on 2007-09-18
Open a terminal (Applications->Accessories->Terminal) and type:
```
sudo dpkg --configure -a
```
and enter your password when prompted.  If this doesn't fix it, post the output that you get from running the command.

[EDIT] PS - If you still have update manager or synaptic open, you will need to close it before running the dpkg command.

---

