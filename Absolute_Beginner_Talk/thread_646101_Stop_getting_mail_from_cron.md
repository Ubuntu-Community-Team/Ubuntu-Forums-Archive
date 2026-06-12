---
title: "Stop getting mail from cron?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-20
I have fetchmail set as a cron job to check my work email every 5 minutes.  However, I'm getting mail from cron telling me that it did it's job.

Is there a way to stop this?

---

### Post by yabbadabbadont on 2007-12-20
Make sure that you redirect the output to /dev/null.

Example: ```
somecommand > /dev/null 2>&1
```

---

### Post by Mramius on 2007-12-20
Ahh, great thanks.

What is the ```
2>&1
```?

---

### Post by yabbadabbadont on 2007-12-20
Redirect standard error as well as standard out.

---

