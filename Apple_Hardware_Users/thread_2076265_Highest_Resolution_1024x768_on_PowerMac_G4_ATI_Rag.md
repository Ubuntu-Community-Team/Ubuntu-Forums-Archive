---
title: "Highest Resolution 1024x768 on PowerMac G4 ATI Rage Pro"
date: 2012-10-25
forum: Apple Hardware Users
---

### Post by jsedwards on 2012-10-25
I just installed Lubuntu 12.10 on two PowerMac G4 machines.  The maximum resolution on both of them appears to be 1024x768.

Both machines have a ATI Rage 128 PF/Pro AGP 4x TMDS graphics card.

The first machine has never had Linux on it before. The second machine had Ubuntu 12.04 on it before.  I don't remember what resolution it had when it had 12.04 on it, but I'm pretty sure it was higher than 1024x768.

I read some previous posts and it sounds like there have been issues with Rage Pro cards and Ubuntu PPC in the past.  Should I revert back to 12.04 and see if the resolution is higher?  Or are there some settings that I can try to increase it?

---

### Post by jsedwards on 2012-10-26
I went ahead and installed Ubuntu 12.04, on the machine that didn't have Ubuntu on it before, and it is even worse.  When I boot it up now, it displays a warning about "Low Graphics Mode" and displays several option buttons.  I've clicked on a few of the buttons and always end up at a TTY login.

So I guess I will reinstall 12.10 and see if I can up the resolution some way.

---

### Post by rsavage on 2012-10-28
Your issues with 12.04 are easily solved.  Just follow the instructions on the PowerPC known issues page.

12.10 has a new acceleration method (EXA) for r128 cards.  It would be interesting to know if this is working (look at logs) and if you see a difference in performance.

See PowerPC FAQ for how to solve resolution problems.

---

