---
title: "[SOLVED] Message: AN Error Occured"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-03-19
Hello Ubunteros!

I tried to launch SYNAPTIC PACKAGE MANAGER and received the following error:

An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I then noticed that the UPDATE MANAGER icon had updates to be downloaded and the same message appeared again.


Is this a serious issue? What is going wrong?

Can someone help me correct it and explain to me what the issue is?

Thank you

---

### Post by handydan918 on 2008-03-19
> **suomalainen said:**
> Hello Ubunteros!

I tried to launch SYNAPTIC PACKAGE MANAGER and received the following error:

An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I then noticed that the UPDATE MANAGER icon had updates to be downloaded and the same message appeared again.


Is this a serious issue? What is going wrong?

Can someone help me correct it and explain to me what the issue is?

Thank you
Well, have you tried running dpkg --configure -a as the message says?

You will need sudo for this, so:```
sudo dpkg --configure -a
```

---

### Post by suomalainen on 2008-03-19
handydan918, thanks for the SUDO instrructions.

I'm still cluleless as to what the issue was and its severity.

Can anyone explain that to me?

Thanks!

---

### Post by handydan918 on 2008-03-19
> **suomalainen said:**
> handydan918, thanks for the SUDO instrructions.

I'm still cluleless as to what the issue was and its severity.

Can anyone explain that to me?

Thanks!

The "severity"
 is high, because you obviously can' t install jack with the problem extant.
The cause could be something as simple as a power interruption while the package manger is running. This message doesn't (or shouldn't!) show up all that often, but it isn't unheard of either. It doesn't necessarily mean you have a systemic problem.

---

### Post by suomalainen on 2008-03-19
Interesting that you mentioned "power interuption". Yesterday, the electric went off for one of those thousands of a seconds deals and everything in the house either got shut off or rebooted.

But I don't believe package manager was running. Or rather have no idea if it was....

I noticed that alnmost evert 30th time I turn on my system Ubuntu doea a "system check" or "something"....

DO this CHECK help issues not occur?

Thanks again for your insight and wisdom!

---

### Post by handydan918 on 2008-03-19
Most modern Linux distros will run fsck at boot time periodically. This does help ensure file system integrity, but I don't think it has anything to do (directly) with your issue.
In any case, if your package manager is working again,it's all good.

---

