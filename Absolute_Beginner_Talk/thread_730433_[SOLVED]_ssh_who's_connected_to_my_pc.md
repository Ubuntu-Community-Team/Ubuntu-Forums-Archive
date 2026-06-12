---
title: "[SOLVED] ssh who's connected to my pc"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by whitethorn on 2008-03-20
Hi, I just set up an ssh server on kubuntu 7.10.  I have it working over my dyndns account, and it's possible to connect to it.  I tried it out with a friend who was also running Linux (I was able to see that he was logged in). I now tried it with my dad he's using WinXP. He's connected to my pc using WinSCP (I know cause we were talking on skype). I don't know why I can't see that he's connected to my server. I tried 

who
who -u

Is there a way to tell if someone is connected?

---

### Post by Dr Small on 2008-03-20
Is he logged in as your account?

---

### Post by whitethorn on 2008-03-21
no he's logged in, using a guest account I set up.

---

### Post by Dr Small on 2008-03-21
Check your auth.log to verify that he did connect and login:
```
cat /var/log/auth.log | grep "guest"
```

---

### Post by whitethorn on 2008-03-21
alright that worked, thanx for the help.

---

### Post by kevdog on 2008-03-21
Dr. Small

Is there a command you could run at root, that would show all the users currently logged into the system through whatever means?  Beyond checking the auth log of course.

---

