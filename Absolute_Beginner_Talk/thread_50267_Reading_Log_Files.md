---
title: "Reading Log Files"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by char on 2005-07-19
Can anyone tell me what exactly is in these log files?  IE, there is a boot log.  How can I set Ubuntu up so not so many entries are made?  OR does it matter.

---

### Post by mad_scientist03 on 2005-07-19
Well, I would say leave the default log settings alone at this point. It may not seem like they're that useful to you now, but some time in the future it may be helpful to have Ubuntu report what's happening as often as it does. If I had to guess, I would say your hard drive is large enough that you don't have to worry about the space the logs are taking up, and Ubuntu uses a rotating log system so that sufficiently old logs are deleted.

If you have time to kill, and you're interested, you should peruse your various log files to see what's happening. The files /var/log/messages and /var/log/auth.log are particularly important, but all of them contain useful information.

---

