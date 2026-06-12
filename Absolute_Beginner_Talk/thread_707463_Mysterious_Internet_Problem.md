---
title: "Mysterious Internet Problem"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-02-25
Two days ago the internet on my computer was working fine, but now it has seemingly just stopped working.  I haven't downloaded any updates at all.  When i start up my computer with an internet cable plugged in, it just tells me no network connection, when there is definitely internet coming from the cord.  Also, when I try to access wireless, it tells me the same thing.  What can I do to correct this? 
Thanks.

---

### Post by TeoBigusGeekus on 2008-02-25
If you're using a router try to reset it.

---

### Post by gali98 on 2008-02-25
Have you tried 
```
/etc/init.d/networking restart
```
That may give you some output that will help you figure out what's wrong.
Kory

---

### Post by sp0nge on 2008-02-25
Hve you checked to confirm the NICs are configured correctly?? I had a similar issure recently and noticed my network changes weren't saved in the network settings for my wireless card. It took a few times of changing the settings and rebooting the machine before the changes finally took and were saved. 

I would also consider trouble shooting all the simple issues first. Swap the LAN cable (highly unlikely, but I've seen it before), connect the machine directly to the modem, review the router settings, and so on.

---

### Post by jordank on 2008-02-25
I've already narrowed it down that it is not a cable or router problem.  I'll try running some of the commands posted above.

---

### Post by jordank on 2008-02-25
Also, how do i check if my NICs are working properly?

---

### Post by Andavane on 2008-02-25
> **jordank said:**
> Two days ago the internet on my computer was working fine, but now it has seemingly just stopped working.  I haven't downloaded any updates at all.  When i start up my computer with an internet cable plugged in, it just tells me no network connection, when there is definitely internet coming from the cord.  Also, when I try to access wireless, it tells me the same thing.  What can I do to correct this? 
Thanks.
errr... if your net isn't working, how did you manage to post your question?
Regards
John

---

### Post by jordank on 2008-02-25
I'll give you 1 guess.
Lol like i don't even know how to reply to that question.
Believe it or not, there is more than 1 computer in the world.
Not to be rude, but that was a bit of a dumb question. lol.

---

### Post by Andavane on 2008-02-26
> **jordank said:**
> I'll give you 1 guess.
Lol like i don't even know how to reply to that question.
Believe it or not, there is more than 1 computer in the world.
Not to be rude, but that was a bit of a dumb question. lol.
You are not rude. Forgive me, but for a large part of the year I live in an isolated
village which only has one computer. I forget myself.
It's probably high time I began to conform with the rest of the world.
Kind regards
John

---

