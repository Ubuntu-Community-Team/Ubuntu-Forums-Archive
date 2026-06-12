---
title: "[SOLVED] SquirrelMail - Unknown user or password incorrect"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-04-07
I have installed PostFix and SquirrelMail.
I can send/receive email from the command prompt but cannot get web-based mail called "SquirrelMail" to work.

Everytime I try to log in, I get "Unknown user or password incorrect".

For the username, I've tried:  carl and [email]carl@Cerant.com[/email]

Any help is appreciated.

Thanks

Carl

---

### Post by cwmoser on 2008-04-07
More information, in /etc/mail.log, these errors appear:
     imapd: LOGIN FAILED, user=carl
     imapd: LOGIN FAILED, user=carl@cerant.com

Both attempts to log in as carl and as [email]carl@cerant.com[/email] failed.

I have SquirrelMail authentication set for "login"

Any ideas?

Carl

---

### Post by cwmoser on 2008-04-08
This was the solution:

[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)

---

