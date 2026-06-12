---
title: "Scheduling with AT"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by snman31 on 2006-05-28
Hi, I'm trying to set streamripper to run at a later time in the day using the AT command.

I've been using at now + 30 minutes, then inputing the streamripper command followed by [EOT] on a seperate line, just like the FAQs say. The job schedules, but when I wait 30 minutes nothing happens that I can see. Is there something else I should be doing?

Thanks!

---

### Post by colo on 2006-05-28
Well, as `at`-Jobs do not have a controlling terminal, your job most possibly is running IN THE BACKGROUND, and you just fail to notice it. You could try monitoring your system with tools like `top`, or a compination of `watch` and `ps` (check the man-pages for those) to find out what's actually going on.

---

