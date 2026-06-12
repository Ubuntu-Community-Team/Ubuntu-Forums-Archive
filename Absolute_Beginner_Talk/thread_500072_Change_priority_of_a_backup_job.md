---
title: "Change priority of a backup job"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Rednarb on 2007-07-13
I have a backup script that runs tar on a set of folders. However when it runs it seems to suck the life out of the machine making all other things run more slowly. Is there a way to lower the priority of this backup job so that it may take longer (which is fine) but will not hog system resources?

TIA,

Eric

---

### Post by zanglang on 2007-07-13
Just prefix your script command with "nice -19". That will increase its "niceness", which reduces its CPU priority as much as possible. For more info lookup the manpages. :)

---

### Post by Rednarb on 2007-07-13
Thanks!

---

