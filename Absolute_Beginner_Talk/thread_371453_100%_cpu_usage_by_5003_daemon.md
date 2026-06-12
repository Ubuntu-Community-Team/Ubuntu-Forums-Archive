---
title: "100% cpu usage by 5003 daemon ??"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-02-26
Any idea what the 5003 daemon is? I ran "top" in terminal and it says 5003 daemon is running consistently at 47 to 65% all of the time. This causes a 100% usage of my cpu all of the time. Any ideas how I can find out what the daemon is or how to kill it?

---

### Post by jerrynewt on 2007-02-27
Got it !! just ran "sudo kill ID (the daemon pid #) and that took care of the problem.

---

