---
title: "Script for automatically running Terminal command?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by josh.on.linux on 2008-01-18
Hi!

I was wondering whether I could automatically run a terminal command at a certain time (e.g. 1:30pm)?

So it would be something like "run command blablabla at 1:30pm."

I am very new to Linux, using the terminal and scripting, but if anybody could give me a hand, it would be greatly appreciated.

Thank you very much!

Joshua

---

### Post by p_quarles on 2008-01-18
Yep. The "at" command will do that for you. 

For instance, to run "df -h" at 5:00 PM you would type:
```
df -h | at 17:00
```See:
```
man at
```for more details.

---

### Post by bwtranch on 2008-01-18
Yeah sure, you can do that. I've never had a reason to do that but, I think it's in the Linux Commands Line List v1.2. I don't seem to have the URL handy, but you can Google for it. It's a good reference and I would recommend printing it out.

---

### Post by josh.on.linux on 2008-01-18
Thank you!  The "at" command is what I was looking for. :-)

---

### Post by thelatinist on 2008-01-18
If you want to run it at that time every day, you might want to look into cron.

---

