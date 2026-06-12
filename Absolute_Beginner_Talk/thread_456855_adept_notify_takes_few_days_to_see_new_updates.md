---
title: "adept notify takes few days to see new updates"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-05-28
i received the e-mail from ubuntu security about new kernel updates on 24th may, and it was only today did adept-notify (I use KDE) tell me that it was available to download... 

My PCs been on (for long periods of time) everyday since (and including) the 24th.

Is there any setting to increase the frequency adept checks for new updates?

I'm quite concerned about this as if it was a remote root exploit I could have been left wide open for 4 days!

---

### Post by tkjacobsen on 2007-05-28
you could make a daily cron job to apt-get update

Make a file in /etc/cron.daily/
named e.g. update.cron
```

#! /bin/bash
apt-get update

```

and then
```
sudo chmod +x /etc/cron.daily/update.cron
```

---

### Post by PetePete on 2007-05-28
thanks, i've already done that for my server (to send various daily status reports)

but thought there might be some setting in a GUI which needed ticking.. 

suppose I was really wondering what trigers the adept-notify to check for updates....
ive seend 2 files in /etc/cron.daily 
apt and aptitude but wasn't too sure what they do, and if my PC is switched off at the time cron daily runs does that mean it wont happen, i think it does..

---

### Post by tkjacobsen on 2007-05-28
I think you are right when you say that they won't run if the comp. is off. I really don't know if there is something else you can do like settings in adept. You have to look for yourself (I'm not on kubuntu right now).

---

