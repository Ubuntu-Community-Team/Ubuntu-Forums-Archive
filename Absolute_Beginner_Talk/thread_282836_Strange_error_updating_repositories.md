---
title: "Strange error updating repositories"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2006-10-23
Hi (again),

I opened up Ubuntu's installer (not Synaptic, the simple one), and it told me it needed to update its repositories.  Fair enough.  However, as it was trying to update them, I got the following warning:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

I'm not sure what this really means and would appreciate anyone's help.

Regards.

---

### Post by bulldog on 2006-10-23
That's not so hard to understand,you don't have a legimate key installed.

By the way,mine is not working too.

Just put a # before the line in your sources.list and you should be fine again.

---

### Post by grim918 on 2006-10-23
I have the same problem. I actually downloaded the key but it still did not work. I am now wondering if it is a problem with the actual repository. Many others are having similar problems with that repository. It used to work about a week ago and then it just started giving problems. Using a comment mark does provide a temporary fix though.

---

### Post by NegativeSpace on 2006-10-23
grim918, bulldog: Okay guys, I appreciate your help.  I suspected it might be something on the repository that's wrong rather than Ubuntu.

Cheers again.

---

