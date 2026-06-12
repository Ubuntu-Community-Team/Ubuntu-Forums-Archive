---
title: "[SOLVED] activate remote desktop from shell"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by ralphz on 2007-12-01
Hi

I have access to my home computer via ssh right now but have no physical access. Is there a way to enable Remote Desktop from ssh shell ?

I have read on this forum that i should look at vino-preferences --help but I don't see any options to set up the password ... etc.

Ralph

---

### Post by ajopaul on 2007-12-01
try ssh -X yourhomeip and then try launching vino-preferences . assuming you are accessing ur home pc from a linux client over ssh. the -X will do a X forwarding..

---

### Post by ralphz on 2007-12-02
Thank you !!!

---

