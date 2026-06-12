---
title: "What is the command that auto execute another command at a certain interval?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-22
Suppose I want to run this command ```
# cat /proc/mdstat
``` every 2 sec automatically, what is the command that must precede the cat command?

Thanks!

---

### Post by win_zik on 2006-08-22
Not exactly what you are looking for, but for monitoring log files you can use tail -f, which will automatically update if the file changes. You can also change the frequency of the updates with -s I think.

Hope this helps.

---

### Post by Iowan on 2006-08-22
> **Akhran said:**
> Suppose I want to run this command ... every 2 sec automatically...**cron**  is designed to run jobs at specific times/intervals.

---

