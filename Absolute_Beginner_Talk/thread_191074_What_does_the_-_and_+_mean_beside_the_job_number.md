---
title: "What does the - and + mean beside the job number?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-06-07
What does the - and + mean beside the job number?

Example:

[5]- Stopped
[6]+ Stopped

These cannot jobs cannot be killed.

---

### Post by Arndt on 2006-06-07
[QUOTE=tux101]What does the - and + mean beside the job number?

Example:

[5]- Stopped
[6]+ Stopped

These cannot jobs cannot be killed.[/QUOTE]

I quote from "man bash" - the last line mentions "-" and "+":
> 
       There are a number of ways to refer to a job in the shell.  The charac&#8208;
       ter % introduces a job name.  Job number n may be referred to as %n.  A
       job  may  also  be referred to using a prefix of the name used to start
       it, or using a substring that appears in its command line.   For  exam&#8208;
       ple, %ce refers to a stopped ce job.  If a prefix matches more than one
       job, bash reports an error.  Using %?ce, on the other hand,  refers  to
       any job containing the string ce in its command line.  If the substring
       matches more than one job, bash reports an error.  The symbols  %%  and
       %+  refer  to  the shell’s notion of the current job, which is the last
       job stopped while it was in the foreground  or  started  in  the  back&#8208;
       ground.   The  previous job may be referenced using %-.  In output per&#8208;
       taining to jobs (e.g., the output of the jobs command), the current job
       is always flagged with a +, and the previous job with a -.


As for not being able to kill them, it seems that while they are suspended, signals sent to them will do nothing. It's when they are resumed that they act (or the kernel on their behalf) on the signals.

---

