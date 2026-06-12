---
title: "Create a email server"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by ccafiero on 2007-07-18
Hello! I'm a new Ubuntu user.

I'm trying to use this distro for a localhost (apache+mysql) to use Joomla and Moodle.

But now I'd like to build a localhost server able to send email by post (from Joomla, Moodle or PHP script) directly.

It's possible for my localhost?

I've seen around in the net that i must use Postfix. I've just install the program as written here [http://help.ubuntu-it.org/7.04/ubuntu/serverguide/it/postfix.html](http://help.ubuntu-it.org/7.04/ubuntu/serverguide/it/postfix.html) 

My php script say "email sent" but nothing arrives in my email box.

Where are my error? Can someone help me please?

Many thanks indeed
ccafiero

---

### Post by Frak on 2007-07-18
I'm pretty sure you have to resolve the DNS adresses through your ISP.
If your asking me how to do that, I don't know, so I'm glad you posted this, I need the help too.

---

### Post by mohnkern on 2007-07-18
Do you have anything in /var/log/mail.err or /var/mail.log?

Also type mailq <enter> and see if you have queued mail.

---

### Post by Frak on 2007-07-18
try
```
telnet mx1.hotmail.com 25
```
if it gives up, your ISP doesn't allow you to send mail, for SPAM reasons, contact your ISP and ask them to open up that port.

---

### Post by silent1643 on 2007-07-18
related
[http://ubuntuforums.org/showthread.php?t=438165](http://ubuntuforums.org/showthread.php?t=438165)

---

