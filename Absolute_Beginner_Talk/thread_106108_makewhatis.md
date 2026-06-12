---
title: "makewhatis"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by cbeshears on 2005-12-19
Does anybody know why the "makewhatis" command won't work in the command line in Ubuntu?

Thanks for you help.  :confused:

---

### Post by gruepig on 2005-12-19
Use "makedb" (which runs regularly out of cron).

---

### Post by cbeshears on 2005-12-19
What is cron?  I'm trying to use the terminal command prompt.  Is this the same?

---

### Post by gruepig on 2005-12-21
Cron is the service which takes care of running routine tasks at certain times (typically daily, weekly, and monthly, though you can also set up processes to run hourly or whenever you choose).  The man/apropos indexes should be getting updated automatically.

And I meant 'mandb', not 'makedb'.  Just type 'sudo mandb' at the command prompt.

---

