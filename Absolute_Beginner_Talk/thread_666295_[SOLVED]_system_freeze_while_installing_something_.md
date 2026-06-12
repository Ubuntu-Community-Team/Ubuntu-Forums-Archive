---
title: "[SOLVED] system freeze while installing something from synaptic - now synaptic won't"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Marianne_S on 2008-01-13
i was installing something using synaptic when my system froze and i was forced to restart the computer. when i tried to open synaptic again i got this error message :

 "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

running  "dpkg --configure -a'"  in terminal - it tells me i need to be a super user to do that. i tried the su command and typing my password - but "authentication failed" - so now i am at a loss - what can   i do?

is there any way to fix this?

---

### Post by overdrank on 2008-01-13
> **Marianne_S said:**
> i was installing something using synaptic when my system froze and i was forced to restart the computer. when i tried to open synaptic again i got this error message :

 "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

running  "dpkg --configure -a'"  in terminal - it tells me i need to be a super user to do that. i tried the su command and typing my password - but "authentication failed" - so now i am at a loss - what can   i do?

is there any way to fix this?

HI and the command would be ```
sudo dpkg --configure -a
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ThrobbingBrain66 on 2008-01-13
Use the following command

```
sudo dpkg --configure -a
```

You'll be asked for your password and everything should work.

EDIT: too late. overdrank, I see you've returned the favor :)

---

### Post by Marianne_S on 2008-01-13
yesssssssss! thanks a million to the both of  you haha :D

---

