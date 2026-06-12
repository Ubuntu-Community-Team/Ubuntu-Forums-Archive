---
title: "process disk io"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by ayu on 2007-12-21
Hello,
Sometimes my disk will spin for an entire 2 minutes while I'm not doing anything, so I would like to know what process is reading/writing to disk.  Neither "System Monitor" nor "top" seems to list the disk io of processes.  Is there a simple way to see what process is accessing the disk?
thanks

---

### Post by nowshining on 2007-12-21
updatedb

any programcs/scripts in the cron scheduler, 

as for system monitor did u set it to show all processes and show dependencies as well?

go to the processes tab

view - all processes

check dependencies

---

### Post by ayu on 2007-12-22
Thanks for the reply.  But even displaying dependencies in System Monitor will not show DISK I/O,   I really hate to compare to windows, but their task manager allows for selecting disk i/o as one of the information fields, whereas I do not see any option in System Monitor.  Again, is there a simple way to see what process is accessing the disk, (and hopefully be able to sort by access throughput)?
thanks in advance

---

### Post by gmayer on 2007-12-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/157191](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/157191) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've been looking for hours for a suitable tool until I came across [this thread on linuxquestions]("http://www.linuxquestions.org/questions/linux-kernel-70/how-to-enable-process-io-statistics-600777/#post2963872") which seems to have all the answers.

To cut a long story short, in order to get *per process* i/o statistics (vs overall i/o stats as reported by vmstat, iostat, saidar et al) the kernel needs to support disk i/o accounting on a process level, something which the CONFIG_TASKSTATS kernel config option provides. However, this isn't enabled on either feisty or gutsy kernels (see related bug).

So you have the choice of waiting for this to be resolved or, if you can't wait, to roll your own kernel with the above option turned ON (get vanilla kernel "uname -r", base your config on /boot/config-$(uname -r) and enable CONFIG_TASKSTATS as well as CONFIG_TASK_IO_ACCOUNTING, haven't done this myself so ymmv).

In either case once you have kernel support for this you need some userland utilities to actually display this data nicely, the bug report has some pointers.

---

### Post by ayu on 2007-12-27
Wow, I can't believe process i/o stats aren't enabled by default.  Compiling my own kernel seems a little more than I want to do, so I will wait and hopefully it will be in the next release.  Thanks for the information anyways! :)

---

### Post by nowshining on 2007-12-30
the process is relatively easy to do.

---

