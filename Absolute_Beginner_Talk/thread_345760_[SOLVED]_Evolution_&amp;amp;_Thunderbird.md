---
title: "[SOLVED] Evolution &amp;amp; Thunderbird"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by azalamo99 on 2007-01-24
I am having a problem  setting up an email client (I have tried both Evolution and Thunderbird). I have searched the forums and checked all set-up parameters. I have changed the Gmail parameters per the setup instructions. I can ping the mail servers, both smtp and pop. What I can do is make it work. I don't get any error msg except the the connection (both smtp and pop) have timed out. Does anyone have any ideas where I need to go next (keep it friendly) :)

---

### Post by teitunge on 2007-01-24
Are you using SSL and TLS?

---

### Post by linux_believer on 2007-01-24
Did you go into gmails settings and enable pop?

if you can receive and not send it is possible your ISP will not allow you to pop another server that is not theirs.

---

### Post by AndyCooll on 2007-01-24
Which instructions did you follow? I download my e-mails in to Evolution without any problems (and I've also previously configured Thunderbird successfully.

Here are some instructions for Thunderbird: [Configuring your email client: Thunderbird 1.5]("http://mail.google.com/support/bin/answer.py?answer=38343")

:cool:

---

### Post by azalamo99 on 2007-01-25
Yes I am using SSL and TSL and yes I have gone into gmails settings and enabled pop. I have followed all the instructions I have been able to find . Nothing has worked so far and I have tried both Evolution and Thunderbird. It has got to be something else than the settings.

---

### Post by bradford72 on 2007-01-25
> **azalamo99 said:**
> Yes I am using SSL and TSL and yes I have gone into gmails settings and enabled pop. I have followed all the instructions I have been able to find . Nothing has worked so far and I have tried both Evolution and Thunderbird. It has got to be something else than the settings.I had this problem before too...here's what worked for me>           Well, I got it to work, and I feel like this is kind of "double dipping" but I thought "hey! it works! maybe someone else can use what I got figured out!" So here ya go....Instead of entering smtp.gmail.com:465 in the entry box for outgoing server, I had to use the numbered version 72.14.247.109:465 is the gmail address for smtp server (outgoing) and that made all the difference in the world...the address for the gmail pop server (incoming) is 66.249.83.111:995 definately DO use SSL encryption for both incoming and outgoing mail. I also selected password authentication for the pop, and login authentication for the smtpgood luck, hope that helps! By the way, use only SSL, not TLS and be sure include the port numbers (:465 and :995) that go with the addresses...Evolution works great for me now that I did that!

---

### Post by Ennead on 2007-01-25
Did you enable POP for your email account online?  You have login to [http://mail.google.com](http://mail.google.com) and enable your account to use the POP protocol.

My Thunderbird server settings look like this:
POP
Server Name: pop.gmail.com
Port: 995
User Name: [email]youremail@gmail.com[/email]
Security Setting: SSL
Server Settings: check the boxes you like
SMTP:
Server Name: smtp.gmail.com
Port: 587
Use Name and Password: yes
User Name: [email]youremail@gmail.com[/email]
Use secure connection: TLS

One other problem I came across is that all my ports below about 1000 were blocked, so I used 1587 for the port, and it worked.  Good Luck. :)

---

### Post by azalamo99 on 2007-01-26
Yes Bradford72, something that finally worked. Thank you so much. I am very grateful for everyones help. This email thing really had me stumped.

---

### Post by bradford72 on 2007-02-13
> **azalamo99 said:**
> Yes Bradford72, something that finally worked. Thank you so much. I am very grateful for everyones help. This email thing really had me stumped.no prob.  Glad that I could help...that makes a HUGE difference in how excited I am about running linux!

---

