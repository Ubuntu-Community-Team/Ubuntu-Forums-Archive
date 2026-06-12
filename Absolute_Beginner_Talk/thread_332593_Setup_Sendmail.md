---
title: "Setup Sendmail"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-01-06
I am trying to install sendmail in Ubuntu Edgy Eft. I installed it with sudo apt-get install sendmail, and it installed fine. Now, I am trying to send a message using this command: sudo sendmail /Emrcheatr@gmail.com "mrcheatr@gmail.com" TESTSUBJECT TEST Message

That should send an email with a reply-to of [email]mrcheatr@gmail.com[/email] and a to [email]mrcheatr@gmail.com[/email]. The subject would be TESTSUBJECT and the message would be TEST MESSAGE. After I hit enter, it prompts me for my password. I enter it, and then I get a blinking cursor on a new line that never goes away. I don't ever get an email.

Could someone help me get sendmail working properly?

---

### Post by raevin on 2007-03-01
If you haven't solved this already...

If I remember correctly, to send an e-mail there has to be a single dot/period (.) at the end of the message on it's own line

[quote="Example"]
(SMTP stuff to not care about)
MESSAGEYAYIES!
.
[/quote]

---

### Post by psylvester on 2007-03-23
root@zion:/usr/psylvester# sudo apt-get install sendmail
Reading package lists... Done
Building dependency tree... Done
Package sendmail is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sendmail has no installation candidate

---

### Post by raevin on 2007-03-23
> **psylvester said:**
> root@zion:/usr/psylvester# sudo apt-get install sendmail
Reading package lists... Done
Building dependency tree... Done
Package sendmail is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sendmail has no installation candidate

Check to make sure your /etc/apt/sources.lst file doesn't have any #'s before any repositories...

---

### Post by sephirothsigep on 2007-04-10
use mutt ore pine instead of sendmail. sendmail is so more move than just a commandline e-mailer. you really dont want to start screwing with sendmail some bad things can happen. and if you try to install from source best of luck.

quote:
your not a linux network admin until you install sendmail from source and you are crazy if you do it again.

---

