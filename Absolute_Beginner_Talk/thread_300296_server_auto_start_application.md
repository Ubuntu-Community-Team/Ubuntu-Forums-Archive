---
title: "server auto start application"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by sunspots on 2006-11-15
I am running Ubuntu Server 6.10 Dapper Drake and have installed sshd.

Now, I want to have sshd to auto start at boot time. I have found information on how to add for start up but they all tell me how to do the job in a desktop environment. The server only has the command line.

eg
[https://help.ubuntu.com/community/AddingProgramToSessionStartup?highlight=%28startup%29](https://help.ubuntu.com/community/AddingProgramToSessionStartup?highlight=%28startup%29)

How do I do it from the command line?

Thanks for any tips or pointers to forum topics.

---

### Post by giants_fan on 2006-11-15
You mean something like...

sudo /etc/init.d/ssh start

---

### Post by sunspots on 2006-11-15
Giants_fan
Thanks for the quick response. I had a look in the directory and found an entry for SSH.

So, I rebooted and found that SSHD started. 

Spent and hour and half looking around for adding  for auto start and didn't need to. Then again ... I now know for the future.

Thanks again.

---

