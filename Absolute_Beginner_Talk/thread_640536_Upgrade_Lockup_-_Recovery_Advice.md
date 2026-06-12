---
title: "Upgrade Lockup - Recovery Advice"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by kscastaway on 2007-12-14
I finally convinced myself to let go of 6.06. Yesterday I began progressive upgrades and with 13 minutes left the Edgy install locked up on wvdial. Task list wouldn’t let me kill it and nothing else worked. I rebooted and got a flashing curser. By escaping to the menu I can get to root in recovery mode or use an older setting to get the message that x-server failed to start as it is not configured properly. I am hoping to salvage this and not have to start again with a completely new install. I’m sure this has happened before and I’m hoping someone more experienced has some salvage advice.

---

### Post by pHreaksYcle on 2007-12-15
I have no clue what's up with this mangled upgrade, but I do have advice! Always do fresh install and just copy and paste your Home folder or just certain things from it. So much easier and less trouble. Hope you get this figured out.

---

### Post by kscastaway on 2007-12-16
With nothing left to lose I just started trying things and found a solution:
On startup hit escape and choose one of the older versions (not a recovery mode this will take you to root)
During the basic signon choose recovery mode
open terminal and run "sudo dpkg --configure -a"
This finished my crashed install.  It is probably possible to run this from root with out the signon but in my case I needed to explore a bit more before I started entering commands.  There are still a few glitches but I hope pushing on to 7.04 will sort those out.

Thanks for the reply; not getting any response can be discouraging.  :KS

---

