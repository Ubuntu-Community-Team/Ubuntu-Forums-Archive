---
title: "Broken Shift &amp;amp;amp; Caps Lock - SCIM?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-03-19
My Shift Keys and Caps Lock keys stop working after a certain amount of time having my Ubuntu 7.10 64-bit system up, after searching these forums I found that others have been having simlar issues and they point to SCIM as the culprit, but I have yet to have found solution to the problem, can anyone point me in the right direction?

Thanks,
-BassKozz

---

### Post by BassKozz on 2008-03-24
**_Fixed: _**
Applications => Other => Keyboard Layout
There wasn't an "Active Layout" selected (don't ask me why, I couldn't tell ya)...
so I added "U.S. English" to the active list and I am not good to go :D

---

### Post by tgice on 2008-05-02
Thanks B/-\ssKozz, this seemed to (at least for now) solve an incredibly frustrating problem that just popped up for me recently the day after doing an in-place upgrade (from Gutsy -> Hardy Heron).

It happened twice so far today.  The first time, a reboot fixed it.  The second time, I got mad (as didn't want to reboot) so I searched a bit and thankfully found this thread.  When I went into my "Keyboard Layout" applet, the "Enable keyboard layouts" checkbox was unchecked and my Active layout *was* correctly set.

All I did though, to solve the problem, was check "Enable keyboard layouts" and hit apply.  I think immediately it was fixed.  I was even able to uncheck that and put it back and have things remain fixed.

The problem *may* have been triggered by using VMplayer (running Windows XP with the Enso Launcher running in it -- I vaguely suspect that may've caused the problem, but don't know for sure; I'm running all kinds of new software in here now, so it could be all kinds of things).

Thanks again.  Hope this helps someone track down what actually happened.

---

### Post by BassKozz on 2008-05-26
The problem still persists, I have to keep manually going into **Applications => Other => Keyboard Layout** and resetting the keyboard layout even if it's already there :confused:

I am also running VMware when this happens although I can't definitively rule that as the culprit because I am almost ALWAYS running VMware (Workstation).

---

### Post by BassKozz on 2008-05-27
Anyone know why this is happening?

---

### Post by red_nail on 2008-05-31
Well, it was happening to me because grandr had mapped the F19 key to some command. My keyboard does not have an F19 key, so my SHIFT keys stopped working. How's that for logic. :) Maybe you are having some similar problem.

So run gconf-editor

Go to apps -> metacity -> global_keybindings and remove keys that don't exist.

---

### Post by BassKozz on 2008-06-02
thanks for the input red-nail, but i just checked and there wasn't anything funny in gconf-editor... apps -> metacity -> global_keybindings :confused:

---

### Post by BassKozz on 2008-06-04
I now have reason to believe that VMware is the culprit of this issue, but I don't know how to best present the issue to VMware's support forums...
I was using my computer all day today without experiencing the problem at all until I launched my WinXP VM using VMware...

Is anyone else experiencing these issues w/ VMware?

---

### Post by BassKozz on 2008-06-05
Found the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195982)

---

