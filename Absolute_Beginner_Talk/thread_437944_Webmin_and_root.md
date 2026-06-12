---
title: "Webmin and root"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by FITorion on 2007-05-09
So I installed Webmin.  I'm trying to set up a web server and Webmin was recomended to me as a good front end gui for apache.  Any way here's my problem...

I can't login to it.  The guys over at Webmin said it's default is set to username=root pass= Whatever my root pass is.

So I come here.  asking how do I figure out what my root pass is?

I saw one thing that said how to set a root pass... but that would enable root... I'd need to know how to disable root again.

Update: They(Webmin) say ask here....

---

### Post by Skrynesaver on 2007-05-09
You can disable root by removing the password string from /etc/shdow for root

---

### Post by dirtboy on 2007-05-12
From a terminal type this:

sudo passwd

There will be 3 prompts after it.  For the first one, type YOUR password.  For the second, type what you want your root password to be.  For the third, type the same thing you typed for the second.  That will change your root password.

---

### Post by stalker145 on 2007-05-12
> **FITorion said:**
> So I installed Webmin.  I'm trying to set up a web server and Webmin was recomended to me as a good front end gui for apache.  Any way here's my problem...

I can't login to it.  The guys over at Webmin said it's default is set to username=root pass= Whatever my root pass is.

So I come here.  asking how do I figure out what my root pass is?

I saw one thing that said how to set a root pass... but that would enable root... I'd need to know how to disable root again.

Update: They(Webmin) say ask here....
[B][SIZE="3"]
WHOA!! Slow down. [/SIZE][/B]

OK, here's the way you need to go. Disregard any advice to enable your root account. The password that you will use is the same password that you use to install programs, make system changes, etc. Basically anything requiring sudo. That is your root password.
I am guessing since you asked about actually logging in that you figured out which port WebMin defaults to (I think it was 10000 or so).

If you have any other questions about WebMin, let us know.

---

