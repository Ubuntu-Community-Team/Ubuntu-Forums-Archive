---
title: "Skipping a job in a script"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-04-26
Is it possible to skip a job while a script is running?  I put many jobs for a script to do, but sometimes, one of the jobs gets trapped in some loop or just keeps trying because the conditions for the job is not met.  So is there a shortcut I can press while a script is running to skip over to the next job?

---

### Post by katu on 2006-04-30
usually you can press ctrl+c to break the current running process. If I remember right inside a script this has the effect of going to the next job. (but it breaks the curent one)
I don't know if this is the solution you were looking for... ;-)

---

### Post by Randomskk on 2006-04-30
If, in the script, you run the job like this:
command &
(ie:
echo "hi" > hi.txt &
)
then it will run the command in the background and get on with the next thing.

---

