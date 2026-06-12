---
title: "wine on gutsy: path not found"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by branch008 on 2007-10-28
Hi,

I'm fairly new to ubuntu and have installed 64 bit Gutsy and 64 bit wine (latest directly from wine hq) .
Most windows apps install fine.  Got the flash going with sound in  64 firefox.:)

However some windows apps won't install because they say they can't write to drive c:
(no permission or path not found).

I'm have this problem with autocad especially.

Can anyone help?
Thanks

---

### Post by Delvien on 2007-10-28
> **branch008 said:**
> Hi,

I'm fairly new to ubuntu and have installed 64 bit Gutsy and 64 bit wine (latest directly from wine hq) .
Most windows apps install fine.  Got the flash going with sound in  64 firefox.:)

However some windows apps won't install because they say they can't write to drive c:
(no permission or path not found).

I'm have this problem with autocad especially.

Can anyone help?
Thanks

Did you run wine with sudo ? or have wine running in the root dir while running with user privs?

Try installing into a folder on /home/USER, see if that works, because if you install yo your root dir, while running with user privs you wont be able to write to /root.

---

