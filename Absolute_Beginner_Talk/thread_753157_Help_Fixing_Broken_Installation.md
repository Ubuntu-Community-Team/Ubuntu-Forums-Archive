---
title: "Help Fixing Broken Installation"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by rjmusto on 2008-04-12
Have recently dual boot installed 7.10 on a Dell Optiplex GX620 and had it running fine.

However, it has just failed to reboot following a suspend and now hangs with the Ubuntu splash screen and the progress bar only just started.

It boots to command prompt in safe mode, but I have no idea what to do after that.

Can anyone point in the right direction as it were? Any good documentation on this anywhere - or do I just re-install?

Thanks,
RM

---

### Post by Inxsible on 2008-04-12
Did you change any configurations before this started happening ?

you might also want to try this command```
startx
```

---

### Post by rjmusto on 2008-04-12
Pretty sure I didn't change anything - though I this could have been the first time I did a suspend.

Tried startx and get a screen full of error messages, eg:

cannot create temp file
error locking authority file
process set to priority -1 instead of requested priority 0
......


(still boots ok into Windows by the way)

---

### Post by Inxsible on 2008-04-12
> **rjmusto said:**
> Pretty sure I didn't change anything - though I this could have been the first time I did a suspend.

Tried startx and get a screen full of error messages, eg:

cannot create temp file
error locking authority file
process set to priority -1 instead of requested priority 0
......


(still boots ok into Windows by the way)Maybe suspend doesn't work the way it should. After you suspended, did you come back to Ubuntu or did you go into Windows immediately after the suspend? 

If you went to Windows, that could also be a source of the problem. Have you tried shutting down and then restarting it ?

---

### Post by rjmusto on 2008-04-12
After the suspend, I tried to boot back to Ubuntu, but was left with a blank screen. Had no choice but to hold the power button and go for a complete restart. Now it hangs as described.
Does the same every time.

---

