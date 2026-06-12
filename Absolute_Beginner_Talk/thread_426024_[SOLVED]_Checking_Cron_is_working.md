---
title: "[SOLVED] Checking Cron is working?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-04-28
I have two Cron related questions. I'm using KCron as I still like the comfort of a GUI!

What I'd like to know is:

- Do I need to do anything to make sure Cron is running at startup? Is it defaulted to that and how can I doublecheck it's still set up that way?
- Is there a way to make a terminal window appear so I can see the Cron job is running?

I'm going to be away for a few days, and want to reassure myself in advance that it's working!!!

Thanks!

---

### Post by dante.regis on 2007-04-28
By default, the cron daemon runs with the computer start. But you can confirm that by placing a job on the cron that writes something to a file, or appending this command to your already made cron job:

echo "Hello World, I'm working" >> /home/myuser/cronlog.txt


Best

---

