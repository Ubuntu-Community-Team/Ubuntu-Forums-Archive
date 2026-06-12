---
title: "[SOLVED] Gutsy made my PC slow!  Why?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2007-11-16
Wow, so what happened?  I upgraded to Gutsy and now my computer takes twice the time to boot up.  Even when I'm just running 1 program, my PC is super slow.  When running something like Open Office and using Rhythmbox, typing trails behind - meaning I type and the cursor isn't keeping up.  (I used to run 3 or 4 programs at once, now it's like the computer is "Overworked" on 2.)

God forbid I should try to play an online game, that's just dreadfully slow.

Just last week I was using Feisty, with no probs, but upgraded because I wanted to get Kdenlive from the repos.  But even typing this, there are spots where the typing "Sticks" a bit.

Any ideas why this has happened?  More importantly, how do I get the thing to run faster?  Or stop whatever process is eating up my speed.

Only differences are, I loaded up Compiz, but according to the system monitor it's not sucking up more than a couple %.

Sure could use some answers if you got em'.  Thank you.

---

### Post by Inxsible on 2007-11-16
try to see in the system monitor or using the top command to see what app is using the most cpu cycles. The pre-installed tracker applet is known to do some indexing in the background and it could be the culprit

---

### Post by Motorhead Kaze on 2007-11-17
Hi again, yes I tried the "Top" option and find nothing that looks abnormal...then again, I mean, I'm no super computer whiz.  Compiz is using between 1 - 2%  Xorg gets in there between 1 - 10% of Cpu usage...I dunno.

---

### Post by adam.tropics on 2007-11-17
As [Inxsible]("http://ubuntuforums.org/member.php?u=71369") said above, tracker has caused a few problems for some folks, **despite** what top reports. Try disabling it and see if it helps.

---

### Post by KIAaze on 2007-11-17
Uninstall tracker, or deactivate it at startup in System->Preferences->Sessions.
If you have Beagle, do the same for it.

That's what worked for me at least.

But as Inxsible said, look in System->Administration->System monitor (the GUI equivalent of top) and sort by RAM or CPU used to see who's the culprit.

---

### Post by shuttleworthwannabe on 2007-11-17
I had the same problem; apps launching was so slow including selecting items from the menus--I found out that it was compiz that did this; uninstalled compiz, now it is running smooth and not hot at all,

S

---

### Post by Motorhead Kaze on 2007-11-17
Hey cool.  And thanks for the location of Tracker so I could disable that.

...yeah, Compiz is giving me lots of **** too.  But I'm only keeping it because it doesn't work yet, and I'm not giving up until it works.  hahaha.

Thanks guys!:)

Compiz really did slow the computer way down for some applications like Flash.  Also, my install of Gutsy didn't gel well I guess.  Flush, wipe, reinstall.  Good.

---

