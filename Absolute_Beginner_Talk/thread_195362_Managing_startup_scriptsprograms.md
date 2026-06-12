---
title: "Managing startup scripts/programs"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by bohboh on 2006-06-12
Could someone put together a simple "how to" that would explain to noobies like myself, how you would go about setting a script, command and/or a program to execute at startup.

I have tried to figure this one out for myself and have come across so many different ways that i am becoming less confident in managing it. It seems like such a simple task.

Is anyone up to the challenge? :p 

What i have come across:

.bash
system > preferences > sessions
rc.d (i think thats right)
any others?

---

### Post by HeavyAl on 2006-06-12
If you just want to execute stuff at startup then just go to System/Preferences/Sessions and click on the Startup Programs tab. You can add stuff from there. No need for editing files in this case.

--edit
Oops, just noticed you have system > preferences > session already listed as something you've tried .. perhaps there is something specific you are trying to accomplish that could be addressed?

---

### Post by bohboh on 2006-06-12
One thing i need:

Well i have apache with sun one asp installed, it all works apart from one minor thing. Due to a change from mysql4 to mysql5, the server requires a file to exist in the /tmp directory. I want to be able to , at startup, execute the following.

sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock 

Now i placed that into sessions and it didnt work, so i created a .bash script, still no joy. I think it has something to do with the fact that it requires sudo level permissions, so when it gets executed, it is effectively waiting for me to enter a password.

---

### Post by nanotube on 2006-06-12
this thread should help:
[http://ubuntuforums.org/showthread.php?t=192271](http://ubuntuforums.org/showthread.php?t=192271)

basically, shove your script into /etc/init.d, then link it with update-rc.d
more details in the thread ;)

---

