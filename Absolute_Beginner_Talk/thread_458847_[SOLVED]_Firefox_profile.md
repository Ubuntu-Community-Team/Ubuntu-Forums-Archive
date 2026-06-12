---
title: "[SOLVED] Firefox profile"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-30
Hi - I'm trying to start the firefox profile manager to get a new profile.

I've tried in terminal with firefox -profilemanager

and I've tried Alt-F2 to run it in there

Both times nothing happens?

Can anyone shed any light on this please?

TIA

---

### Post by bmagyarkuti on 2007-05-30
the Linux command line is case sensitive. Try this:
```
firefox -ProfileManager
```

---

### Post by forestpixie on 2007-05-30
Yea - thought so - so had tried all permuatations and still no joy. I have a firefox bug apparently, perhaps that's causing it.

thanks though

---

### Post by crossedout on 2007-05-30
Firefox's profile manager won't start if a FF process is already running.  You could check to make sure all occurrences are closed and try again or simply reboot to clear out any processes.  The -profilemanager should work after that.

-Xout

---

### Post by forestpixie on 2007-05-30
Thanks for that - but I'd tried that as well!

Thinks I'll just wait and see what's going on with the bug - that seems to have killed epiphany too.

If ff goes belly up completely I'll use opera I guess

At least something actually gets done with this OS - be waiting for thousands of other errors if I was still using win!!!

:)

---

### Post by forestpixie on 2007-06-02
Updated ff using script I found and Profile Manager worked.

---

