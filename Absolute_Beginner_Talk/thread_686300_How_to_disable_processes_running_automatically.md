---
title: "How to disable processes running automatically?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-02-03
Hi.
I noticed that PostgreSQL is running automatically on my Ubuntu.
How to disable this? and how to stop automatically running processes in general? 
Thanks.

---

### Post by jan quark on 2008-02-03
have a look at sessions
system > administration > sessions

can you uncheck it there so that it doe not load at start up

or just try this

[http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/](http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/)

---

### Post by HuBaghdadi on 2008-02-03
Using 
system > administration > sessions
Doesn't get all running processes (It doesn't list PostgreSQL in my case).
In addition, I don't to kill process by hand, I want to disable some services by default.
Any ideas?
Thanks again.

---

