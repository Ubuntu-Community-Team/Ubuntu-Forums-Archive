---
title: "Power manager won't suspend desktop  monitor (Feisty)"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by jamere on 2007-11-11
Hi all, 
Power Manager doesn't consistently suspend my desktop monitor (in Gutsy) after disuse.  Worked fine in Feisty. It does seem to suspend every once in a while, however.  I set the Power mgt preferences to put the monitor to sleep after 11 minutes of disuse. Power Mgr is enabled in Session Start up and its listed in the current session.

Is this a known issue in Gutsy? Any ideas?

Thanks much,
Jim M

---

### Post by nrfool on 2007-11-11
I used to have similar problems, except that my monitor never shut off. The command
xset +dpms
xset dpms force off   //this command will force the monitor off
Hope it helps you too

---

### Post by jamere on 2007-11-11
nrfool,

thanks for the reply...nice to know...I'll give it a try. I could easily be wrong, but I think there's something buggy in Gutsy program-manager. Worked fine in Feisty.

jim m

---

