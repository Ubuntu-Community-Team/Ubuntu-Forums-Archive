---
title: "Computer shuts itself down overnight"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by veebee on 2007-07-05
Hi,

running four boxes on kubuntu64 bit and generally have no problems, except;

a few weeks ago, my e4400, 1x1GB667DDRII,  (oc'd to 2.87Ghz) running kub x64 7.04

would shut down sometime during the night, did it about 4 nights in a row.

This is a prob because I have them all crunching away madly at boinc projects. It hasnt done it for a little while, but has done it again last night.

7 hours offline equates to around 8 - 900 credits but more annoyingly, I cant work out why it is doing it !!

I had a look at KSyslog but there were no entries past 23.49, then my reboot at 7 am.

A few entries prior to shut down, "cron" ?? any ideas anyone?

Thanks
VB

---

### Post by Raineer on 2007-07-05
Well, cron is the program that runs a script hourly/nightly/weekly by default.

Take a look at the files under /etc/cron.daily.  These are being run automatically every night (probably at midnight).  Some of them are typical maintenance tasks, but I imagine one of them is failing hard, or somehow causing a reboot.

Possibly move the files out of that directory (back them up, don't delete!) and see if not running the scripts will help it.

---

### Post by veebee on 2007-07-05
will removing ALL the details (after backup of course) from that file cause any probs by "them" not being run at those scheduled times?

I wonder if that is it though, considering it has been running fine for the last cpl of weeks...

but I shall try your suggestion

---

