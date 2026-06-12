---
title: "How to wipe home directory?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by dph948 on 2007-11-29
So, I installed Ubuntu (Gutsy) a couple weeks ago, and it has been amazing.  However, recently disaster struck.  A user, very unaware of Linux, who "desperately needed computer access" was added on to the computer, albeit reluctantly.

Earlier, the computer ceased functioning.  After much struggles, I got the computer working, and found on his account "Install_AIM.exe"  which I assume is the culprit of this madness.

I deleted his account, but upon further discussion with other Linux users, I was advised wiping/deleting his home directory would be the best option.  Have I done that when deleting his account?  Is it too late?  If the answers to both of those are "no" then could you guide me through the process?

Thank you

---

### Post by -grubby on 2007-11-29
You might have deleted his home directory when removing his account, but if not, then type

```
gksudo nautilus
``` into a terminal, navigate to the /home directory and remove his directory

---

