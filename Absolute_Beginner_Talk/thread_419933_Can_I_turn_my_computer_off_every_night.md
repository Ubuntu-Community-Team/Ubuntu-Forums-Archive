---
title: "Can I turn my computer off every night?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by waldschm on 2007-04-23
I remember hearing when OS X came out that there were issues with tasks scheduled by cron not being run because people turned their computer off every night. My question is, is this an issue in Ubuntu or is anacron properly configured to let me turn off my comp all night every night?

---

### Post by MasonM on 2007-04-23
That depends on what tasks are set up as cron jobs and what time they are set to run. As long as nothing is set to run during that time there's no reason you can't turn off the machine. worse case those cron jobs simply won't run during that time.

---

### Post by waldschm on 2007-04-23
Hmm, yes well that's sort of what I was asking. If maintenance utilities are set to run during the night, is anacron in ubuntu configured by default to account for that? Given my anacrontab file has never been modified and  looks like this:

# These replace cron's entries
1       5       cron.daily       nice run-parts --report /etc/cron.daily
7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly

Am I able to turn my computer off every night and say for example still have my locate database get updated?

---

### Post by imon9 on 2007-04-23
though i am not sure how to answer you that question: but why not try scheduling a job whcih execute like every ..say 2 minute...and shut down ur comp..then see if it still works after reboot

i always do those experiment when i am not sure :p

---

