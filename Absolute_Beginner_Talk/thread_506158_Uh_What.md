---
title: "Uh What?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by onlinerandy on 2007-07-21
I keep getting this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was trying to install limewire and the install failed. Now I keep getting the above message.

Can anyone help me?

---

### Post by forestpixie on 2007-07-21
go to terminal and run

```
sudo dpkg --configure -a
```

---

### Post by ugm6hr on 2007-07-21
I think this happens if the computer shuts down, or is interrupted during installation of a program.

I had something similar, and eventually made a worse mess and reinstalled.

---

### Post by onlinerandy on 2007-07-21
Ok now I'm getting:

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

---

### Post by forestpixie on 2007-07-21
I think you get a "broken" option in syanptic when there is one - not sure about Kubuntu and Xubuntu - that will allow you to fix or remove it

---

### Post by davidjmayo on 2007-07-21
> **forestpixie said:**
> I think you get a "broken" option in syanptic when there is one - not sure about Kubuntu and Xubuntu - that will allow you to fix or remove it

open synaptic (system==>administration==>synaptic package manager)
click edit 
then fix broken packages

---

