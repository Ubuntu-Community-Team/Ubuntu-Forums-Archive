---
title: "Lose time in Ubuntu, gain time in XP"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by IndyBob on 2007-04-16
Well, I have a strange situation.  I have Ubuntu 6.10 Edgy installed on master and Windows XP on Slave and both are loosing/gaining 4 hours even.  Ubuntu looses 4 hours and XP gains 4 hours everytime I boot into either one.  I can Sync with internet time in Ubuntu but not XP and the time will not hold on either OS.  Any suggestions?  

I have searched XP forums and can't find any solutions that work, but being new to Ubuntu I thought maybe someone else has run across this situation.

---

### Post by talcite on 2007-04-16
How's your bios clock? I'm not sure if Ubuntu and XP still sync to the hardware clock. Check by following instructions to enter setup/bios as soon as you boot up. 

If the clock is your problem, changing the button cell battery on your motherboard should remedy it.

---

### Post by IndyBob on 2007-04-16
That could be it, as my 'puter is a 1998 version Dell and that could be the problem.  I will try getting into the Bios tomorrow and see what that says.

---

### Post by confused57 on 2007-04-16
> **IndyBob said:**
> Well, I have a strange situation.  I have Ubuntu 6.10 Edgy installed on master and Windows XP on Slave and both are loosing/gaining 4 hours even.  Ubuntu looses 4 hours and XP gains 4 hours everytime I boot into either one.  I can Sync with internet time in Ubuntu but not XP and the time will not hold on either OS.  Any suggestions?  

I have searched XP forums and can't find any solutions that work, but being new to Ubuntu I thought maybe someone else has run across this situation.

I think you need to set UTC=no in Ubuntu:

[http://ubuntuforums.org/showpost.php?p=698200&postcount=5](http://ubuntuforums.org/showpost.php?p=698200&postcount=5)

---

### Post by hush on 2007-04-16
> **confused57 said:**
> I think you need to set UTC=no in Ubuntu:

[http://ubuntuforums.org/showpost.php?p=698200&postcount=5](http://ubuntuforums.org/showpost.php?p=698200&postcount=5)

yep, i had this same problem and that UTC thing is what fixed it.
give it a try

---

### Post by IndyBob on 2007-04-16
Just tried it.  I can tell you that once I changed the UTC to no and did a sync to time servers, my screen did not go blank and sit there for a while then once I wiggle the mouse it would come back.  So maybe that's the answer.  I will be back if that doesn't do it.  I also went into my bios this morning and reset the clock on the bios as it was 4 hours ahead.  I may be due for a new battery, but I am hoping this cures the problem.

---

