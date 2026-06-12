---
title: "How to Read Logs..."
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-07-22
I am trying to learn how to understand logs but I am having trouble. Does anyone know somewhere where I can read about the subject. Everytime I look at the logs it has a bunch of stuff that I dont understand what it means. Thank you for any help.

---

### Post by taurus on 2006-07-22
What logs are you talking about?  Are you talking about those log files in /var/log like messages, lastlog, etc.?  Try something like this from a terminal!

```

sudo more /var/log/messages

```

---

### Post by Third Thoughts on 2006-07-22
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

Is a huge linux tutorial. Its got a section on log files in it. Its also got information on just about everything else Linux you could want. Its somewhat dated at times, but def a good resource.

~Andrew S.

---

### Post by grim918 on 2006-07-22
im talking about the user.log and the auth.log in the /var/log directory.
Then there is also the access.log and the error.log in the /var/log/apache2 directory. I can't understand what it is that they say. Thank you for any help.

---

### Post by Third Thoughts on 2006-07-22
> **grim918 said:**
> im talking about the user.log and the auth.log in the /var/log directory.
Then there is also the access.log and the error.log in the /var/log/apache2 directory. I can't understand what it is that they say. Thank you for any help.

I'm not entirely sure about what the user.log. The auth log describes all the users on the system and when they log in/execute certain commands whatever. This includes when a users executes a sudo command, or when background process run with privilleges. I don't know much about apache so I  an't really help you there. 
In general though, the route to understanding the logs is understanding the system itself. If you want to understand the apache stuff consult the apache manual. If you want to understand the Linux stuff read up on the nuts and bolts of Linux.

~Andrew S.

---

