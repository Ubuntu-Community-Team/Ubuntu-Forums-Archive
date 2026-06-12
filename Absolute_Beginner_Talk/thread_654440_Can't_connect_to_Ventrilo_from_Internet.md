---
title: "Can't connect to Ventrilo from Internet"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by MoriyaMinakata on 2007-12-31
As the topic says, went I start a Ventrilo server, internet users cannot connect after a certain period of time. 
After about 10 minutes, only LAN users can connect.
Any ideas anyone?
Thanks.
~Moriya

---

### Post by Dark Hornet on 2007-12-31
Do you have a timeout setting set?  Just a thought....

---

### Post by MoriyaMinakata on 2008-01-01
I thought of that JUST before looking here.
There was a timeout set in the ventrilo settings.
Gonna see if that makes a difference...its still up for now.

---

### Post by MoriyaMinakata on 2008-01-01
Nope.
Same problem.
It lasted 15 minutes this time.

---

### Post by MoriyaMinakata on 2008-01-01
Here is what I get when I type lsof -n -i -P
ventrilo_ 9452 moriya    4u  IPv4  33479       TCP *:3784 (LISTEN)
ventrilo_ 9452 moriya    5u  IPv4  33480       UDP *:3784 

netstat -ln:
tcp        0      0 0.0.0.0:3784            0.0.0.0:*               LISTEN   

I set TCP and UDP cuz I am not sure what Ventrilo uses.
It says its listening on 3784 but internet users still can't connect.
Is there something I am missing?

---

### Post by MoriyaMinakata on 2008-02-08
Bump
Still having this problem.

---

