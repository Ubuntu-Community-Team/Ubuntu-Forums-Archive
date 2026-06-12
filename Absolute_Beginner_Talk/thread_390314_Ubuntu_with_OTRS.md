---
title: "Ubuntu with OTRS"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Rainmaker_mail on 2007-03-21
Dear all,
First of all, i apologize but i am a newbie to linux. I am having a bit of a problem installing OTRS on my Ubuntu 6.10 Server PC. 

I did a LAMP installation via the server CD and then apt-get update & upgrade the packages. Then i ran apt-get install otrs2. It ran and installed alright but nothing happens.

There is no setup screen or anything. Am i missing something?

I have looked at
[http://www.debianadmin.com/how-to-install-otrs-open-source-ticket-request-system-in-debian.html](http://www.debianadmin.com/how-to-install-otrs-open-source-ticket-request-system-in-debian.html)
but again, i am supposed to get a setup screen which didn't pop up.

Oh, i should mentioned that i am using Virtual PC 2007 to create the Ubuntu server.

Thanks in advance,
Rgds,
RM

---

### Post by halitech on 2007-03-22
seeing this has got me trying it as well and I don't get the database setup screens either. Would make alot of my work easier if it would work. 

Any ideas anyone?

---

### Post by cocotu on 2007-03-23
Having the same issue guys! I had to do a: apt-get install otrs NOT otrs2.  otrs2 was not found in the repositories.

---

