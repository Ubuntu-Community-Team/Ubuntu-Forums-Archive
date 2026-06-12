---
title: "S3 Savage4 and Compiz (Fusion)"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by escron on 2008-02-05
Alright now,
prior to posting anything - I've spent about 3 or 4 hours searching for a solution via Google and different forums, but always ended up in threads consisting of pure techtalk. As I'm a bloody beginner I don't dare using a seemingly old solution and editing kernel headers by using bash commands I don't actually know.

So excuse me if there's already been some solution I've missed. Just redirect me there or something.

Anyway, enough malarkey, let's get to the actual problem: I'm trying to use Ubuntu 7.10 on an old Gericom X5 (i486 chipset) and got everything working fine so far apart from some minor problems (such as amaroK using the wrong engine and thus messing up the sound) everything's in good shape. If there wouldn't be this old on-board GPU o'mine, a S3 Savage4. Albeit Ubuntu comes natively with working drivers (simply named 'savage' in the setup tool) and both 3D and DRI support should be possible and enabled I'm not able to get Compiz working. Any other but the minimal interface just won't activate.
So obviously the Savage4 is on some kind of blacklist. I tried skipping the blacklist, yet still no magnificent GUI for me, the installation just aborted a few steps later.

Now I got myself asking..should I really try and recompile the video drivers (as described in [several threads](http://ubuntuforums.org/archive/index.php/t-75393.html) in this forums) to enable DRI or will I just end up messing with my system's guts for nothing?

I'll gladly supply you with any possible information about my configuration, just drop a line what I'm to execute using the Terminal.


Thanks in advance, and excuse the gibberish.

---

### Post by escron on 2008-02-05
Some research later I've come to the conclusion that simply installing an appropriate driver and recompiling my kernel using this new driver would help. Yet even the original [Xorg Savage driver](http://linux.die.net/man/4/savage) is supposed to support 3D, so there wouldn't be much of a difference after all I s'pose.

Well, obviously Linux isn't even sure what kind of card I'm using, The device manager tells me it's a ProSavage 8, the graphics manager says it's supposed to be a Savage4.

---

### Post by ben@layer on 2008-05-03
same here HELP!!!!

---

