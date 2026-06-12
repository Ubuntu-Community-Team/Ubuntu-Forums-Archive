---
title: "Evolution Mail"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by monken on 2007-05-28
I am unable to send on evolution mail only receive, help?:

---

### Post by irish_flu on 2007-05-28
When you can receive mail but not send, the problem is related to your "SMTP server" (sometimes called an "outgoing mail server".

I'm not too familiar with Evolution, but assuming it works like anything else: in your account setup, you'll have the option to set both an incoming (POP3 or IMAP) server and an outgoing (SMTP) server.

What you'll need to do to fix it is find out what your ISP's SMTP server is called.  Check the setting before you call them, and make sure it's not just a typo.


For instance, many ISPs will use mail.xxwhateverxx.com as the incoming server, and smtp.xxwhateverxx.com as the SMTP server.  Others use mail.xxwhateverxx.com for both.  These are just examples, though.  Check out your ISP's website, or give them a call, and you should be able to find the correct info.

---

### Post by seetho on 2007-05-28
Most SMTP server require authentication, i.e. you need to log in to be able to send mail.  Normally this is the same username and password as your POP3 account.

---

