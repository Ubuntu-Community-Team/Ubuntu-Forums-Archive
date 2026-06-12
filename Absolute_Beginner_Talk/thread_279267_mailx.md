---
title: "mailx"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by FoggyMtn on 2006-10-17
Hey Ya'll

I was contemplating ubuntu as a mail server.  To get the ball rolling, I installed postfix and mailx.  I tried to email (from CLI) admin@localhost from root@localhost.  When done in verbose mode, it says it will be delivered.  The only problem is when I check admin's acct, it says no mail.

There seems to be no troubleshooting help for mailx, as it just works... only mine doesn't!  How can I find the break in the loop? And this was supposed to be the easy part! lol

Anywho, how can I set it up so I can email from one user to another on the same machine?

FWIW, I also tried using 
telnet localhost 25
ehlo localhost
mail from: root@localhost
rcpt to:admin@localhost
data
Subject: XX
.
quit

it saysit has been delivered, only still no mail

Any thoughts?

Thaks
rob


on edit, got it, something was screwy in Postfix

Thakns
rob

---

