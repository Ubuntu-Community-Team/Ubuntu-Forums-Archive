---
title: "[SOLVED] Maintenance Questions"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Ancient One on 2007-11-24
On my Mac 10.4, there are several maintenance scripts that need to be run.

1. They are the cron controlled daily, weekly, monthly scripts. Do such animals exist in Ubuntu and do they need to be run?
2. On the Mac you are able to get to a command prompt before the local disk mounts. This enables you to run a fdisk to check that nothing is wrong. Does this need to be done and can this be done in Ubuntu?

3. After installing software, do you have to "fix" file permissions? On the Mac you could run that script whenever you wanted.

4. Sorry to use my Mac (I no longer own) as a reference point, but that was my first exposure to *nis. Does any one know how to search the man files for help on these issues?

Thanks, an old but new user.:confused:

---

### Post by marco123 on 2007-11-24
1. Any cron jobs are run automatically.

2. Ubuntu will automatically check the filesystem every 30 mounts.  

3. I've never had to.

4. man <name>  e.g. man fdisk

Welcome to the community.:)

---

### Post by Ancient One on 2007-11-24
WOW, thanks for the speedy reply. FWIW, I sure am glad that I decided to try Ubuntu. I really did not care for Windows, even though I have had it on numerous machines at home. The install is a piece of cake and it just works! I do have one other question; how can I contribute $ to the cause without going through Paypal? Currently, there seens to be an issue with PayPal and ad.doubleclick.com. 

Thanks again.

---

### Post by Ancient One on 2007-11-26
One more little technical question.

On the Mac, cron would get very confused if the machine was shut off. The maintenance scripts would not run because cron would lose track of the last time they were run and start counting the time until the next run from when you turned the machine back on.

Does Ubuntu have the same problem? If so then I probably would want to run the maintenance scripts by hand.

Thanks again.

---

