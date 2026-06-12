---
title: "Freezing on startup once in a while"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by seraph741 on 2006-08-14
I am brand new.  I have both windows and ubuntu installed on seperate partitions.  When i boot ubuntu, once in a while it runs fine, but most of the time the intro music cuts off and it is basically frozen.  i can do a few things like left click, but i can't click on any buttons or run any programs.  any1 have any clue?

Also, when it does work, the sound doesn't.  Even though it does work at the login screen and when it is booting!

Let me know!  I would greatly appreciate some help!

---

### Post by Darrena on 2006-08-14
> **seraph741 said:**
> I am brand new.  I have both windows and ubuntu installed on seperate partitions.  When i boot ubuntu, once in a while it runs fine, but most of the time the intro music cuts off and it is basically frozen.  i can do a few things like left click, but i can't click on any buttons or run any programs.  any1 have any clue?

Also, when it does work, the sound doesn't.  Even though it does work at the login screen and when it is booting!

Let me know!  I would greatly appreciate some help!

Can you hit ctrl+F1 to drop to a console and look at /var/log/syslog and see if there are any error messages?

cat /var/log/syslog

---

### Post by seraph741 on 2006-08-14
contro-F1 doesn't seem to do anything, is there any other way to debug this problem?

---

### Post by seraph741 on 2006-08-15
another maybe related question.  my internet in ubuntu does not seem to be working anymore.  it was at first, but now it just plain doesn't work.  did i stop some process by accident or something?  when i do a ping in network tools, it works fine.  but i can't bring up any website or download any ubuntu updates.

---

