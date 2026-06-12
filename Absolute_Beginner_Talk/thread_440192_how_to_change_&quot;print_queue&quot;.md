---
title: "how to change &quot;print queue&quot;"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by afonit on 2007-05-11
how do you change/enter in the print queue for a printer that you have set up?

I am using the latest ubuntu.

(yes, I have gone through the printer setup several times, and I do not see it in there)

also,

by the print queue I do not mean to see what is printing, but the 'print queue' in the software, I know this was there back when I tried Ubuntu a couple of years back, but I do not see it as an option now.

---

### Post by dstew on 2007-05-11
What exactly are you trying to do? To see the print queue using the command line, try **lpstat**. To kill a job, on the command line use **lprm *jobid***. The *jobid* is from the lpstat command result.

---

### Post by afonit on 2007-05-11
it is the queue that the computer sends the job to

normally the driver will automatically enter this when it talks with the printer

on windows you can go in and modify the 'print queue' in the printer properties dialog.

like the printer name may be hp 4550, but the print que is hp4550_s5_Print

---

