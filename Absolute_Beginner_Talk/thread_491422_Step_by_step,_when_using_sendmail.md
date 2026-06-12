---
title: "Step by step, when using sendmail"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-07-03
Greetings,
I am quite a newbie at using sendmail, yet I would like to have it because I am programming with Php and using the mail() function and want to be able to send emails with sendmail.

Is there any step by step tutorial or instructions on how to set it up, just for use of the mail() function? I'm only going to use it for that, and I really need help, as I've been reading and can't find any way to install it to get mail() to work.

Your help would be appreciated!

Dr Small

---

### Post by Malibu Illusion on 2007-07-03
I'm not too sure how far you've got on your own here, you don't really say, but a common thing that's missed is not ammending the php.ini file to include the sendmail path.

Open /etc/php*X*/apache*/php.ini, look for this line:

```
; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
;sendmail_path =
```

Remove the semi-solon in front of it and include the path.  The path to the .ini ifile will depend on where PHP is installed and what version you have, but you get the idea.

Take care.

---

### Post by Dr Small on 2007-07-03
I had read on another thread, and had indeed install sendmail, and also, I have edited my php.ini file from /opt/lampp/ect/ (as I have xampp installed), removed the semicolon and placed it in like this:

> 
[mail function]
; For Win32 only.
SMTP = localhost

; For Win32 only.
;sendmail_from = [email]me@localhost.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t

And I've tried it without the -t argument also, and I'm guessing that is the location of sendmail. Other than that, I have no idea what to do, and I still can't get mail() to send anything... :S

And yes, I have restarted xampp.

Dr Small

---

