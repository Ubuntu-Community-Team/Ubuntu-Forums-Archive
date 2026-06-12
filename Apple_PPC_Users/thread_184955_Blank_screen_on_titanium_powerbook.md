---
title: "Blank screen on titanium powerbook"
date: 2006-05-30
forum: Apple PPC Users
---

### Post by shriver on 2006-05-30
I installed dapper via the netboot option on my titanium powerbook (the cd rom drive is broken). The install went through all the way, and succesfully completed, but when I attempt to boot into Ubuntu, the screen flashes white, black, white again, then goes black and stays that way. Other than the glowing apple on the back of the screen, there is no way to tell that the computer is even on. I can still boot into Mac OS X, just my Ubuntu install won't boot.

Has anyone seen this problem before? Is there anyway to boot into a safe mode or diagnose the problem?

EDIT: If I wait a few minutes, eventually, the computer starts to boot linux. I think it may be that the computer is waiting for my busted CD to time out.

Thanks

---

### Post by procras on 2006-06-06
Maybe your console screen is not showing up?
Do you only see the ubuntu login screen (gdm) when it eventually boots?

Yaboot is probably loading and prompting you for a response, when you do not reply it is applying a sensible default.

Normally the prompts would be
First Boot either MacOS Linux or CD
Press l for Linux

Then you need to type Linux to boot your kernel

Once you are booted up look at the options in /etc/yaboot.conf to seen what you might need to set. man ybin too.

Good Luck!

---

