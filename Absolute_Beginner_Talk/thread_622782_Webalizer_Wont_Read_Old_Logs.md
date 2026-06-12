---
title: "Webalizer Wont Read Old Logs"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-11-25
I have Apache2 running with Webalizer on my server but today when webalizer ran it jsut read from the new apache log which was started this morning and lost all the history from my old log. I set up a script that merges access.log and access.log.1 and set webalizer to run on it but i get this output:

```
1338 records (1325 ignored) in 8.00 seconds, 167/sec

```

and it just shows the info from the latest logs.

Does anyone know how to fix this so it runs on my old data aswell as my newer data.

---

### Post by bobbocanfly on 2007-11-25
Sorry but *bump*

Anyone know how to fix this? Been annoying me all day.

---

### Post by punong_bisyonaryo on 2008-03-12
Were you able to solve your problem?

I'd like to ask you about this, a bit different though. I just installed webalizer on an old server, and it has old old logs (access.log.30.gz, etc.). How do I configure Webalizer to read all logs? Currently it is set to read /var/log/apache2/access.log.1.

---

