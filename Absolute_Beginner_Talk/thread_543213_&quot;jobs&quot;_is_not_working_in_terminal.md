---
title: "&quot;jobs&quot; is not working in terminal"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by manuj on 2007-09-04
Hi,
please need help!!!!!

The 'jobs' command doesn't give me any result.
I am logged in as a root user.

I need to know the jobs that are running so that I can stop the job/jobs that I want to.

---

### Post by jorgesallum on 2007-09-04
Please, post error message. If there's no message, type "vim test" and ctrl+Z and then "jobs"

---

### Post by manuj on 2007-09-04
Thank You jorgesallum,


So, 'jobs' will only show jobs that are currently not responding or are stopped.
It will not show system processes running in the background.

Also, when I execute 'man jobs' I get the error:
                  No manual entry for jobs

Why is that?

---

### Post by dwhitney67 on 2007-09-04
Use the 'ps' (process status) command to view running jobs.  For example:

[FONT="Courier New"]$ ps -ef[/FONT]

If you want to kill a process, then issue the following command:

[FONT="Courier New"]$ kill <pid>[/FONT]

where <pid> is the process ID.  If you do not own the process and want to kill it nevertheless, then precede the command with 'sudo'.

Alternatively, you can use this command to kill a process (and all others with a similar name):

[FONT="Courier New"]$ pkill <process name>[/FONT]

If after issuing a 'kill' or 'pkill' and the process does not die, then kill it with extreme prejudice:
[FONT="Courier New"]
$ kill -9 <pid>[/FONT]

---

### Post by asmoore82 on 2007-09-04
> **manuj said:**
> Thank You jorgesallum,


So, 'jobs' will only show jobs that are currently not responding or are stopped.
It will not show system processes running in the background.

Also, when I execute 'man jobs' I get the error:
                  No manual entry for jobs

Why is that?

**jobs** is a BASH shell builtin command for bookeeping of processes created
by that particular instance of the shell

---

### Post by manuj on 2007-09-04
Thank you all for your help.



I love Linux
Love this community.


Thank You.

---

