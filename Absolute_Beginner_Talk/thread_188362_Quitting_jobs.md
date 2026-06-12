---
title: "Quitting jobs"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-06-04
When I type 'jobs', I see some have stopped and continue to occupy a number.  How would I quit a job?

And why does it continue to say it is an active job even though I quit the app?

---

### Post by ape on 2006-06-04
From a terminal, issue the command `kill %<job number>`.  So, for instance, if the result from jobs is:

  `--> jobs
[1]  + suspended  osd_cat`

Then you would type `kill %1`

If the status shows active when you've quit the program, I would start by asking which program it is and how did you quit it?  Successfully exiting a program should result in the job going away.

--Ape--

---

### Post by tux101 on 2006-06-04
Thanks!

Stuff like vim.  I quit using Ctrl+z.

---

### Post by ape on 2006-06-04
Using ctrl+z does not quit the application, but rather sends it into the background (where the process remains active).  For vim, you should just use :q! to exit properly.

---

### Post by taurus on 2006-06-04
The next time you use <Ctrl>z to send something into background but want to kill it, try (from the same terminal that you did <Ctrl>z)
```

kill %

```

---

### Post by IYY on 2006-06-04
To find the process number, I usually use

ps aux | grep <name>

and then to kill it, I use

kill -9 <number>

---

### Post by ape on 2006-06-04
You can also use `jobs -l` which will print out the PID along with the job number.

---

