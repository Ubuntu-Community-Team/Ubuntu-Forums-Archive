---
title: "Is there a way to set a sleep schedule for my computer?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by shutupchuck on 2007-04-05
I was wondering if there was any way to write a program or somehow configure my system so that I could set a "sleep schedule" for it.

For example:
I want it to go on standby at midnight every night and wake itself up at 6 in the morning. 

The reason I want to do this is because I am running an apache server off of my machine and the machine is in my room. It's pretty loud and I would like to be able to have some quiet time every night. The only problem with doing it manually is that I would never remember to turn it back on. Plus, I would like to be able to tell the patrons of the site that it will be unavailable from X at night to Y in the morning instead of it being a random thing. 

I was also thinking maybe there was a way to wake up the computer via an external prompt. Like I could just set it so the machine goes on standby after an hour of inactivity  but then when someone tries to access the site it wakes up. 

If anyone has any ideas I would really like to hear them. Thanks in advance. These forums are always so helpful.

---

### Post by mssever on 2007-04-05
Going on standby should be simple. Simply set up a cron job to run whatever command you need to run to put your computer to sleep. Waking is more problematic. I don't think that it's possible for a cron job to wake your machine up. Many BIOSes have a wake on LAN feature. I don't know anything about that, but it might be what you need, judging from the name.

Another option would be to spin down your hard disks using hdparm. This would quiet your machine down some -- enough maybe? If you combined that with switching off networking via cron, then you could probably make sure that your hard disks didn't wake up early.

---

