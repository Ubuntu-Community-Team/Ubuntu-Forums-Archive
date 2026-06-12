---
title: "How to used command line to receive and send email via remote pop and smtp?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by mellibra on 2006-05-25
I just saw someone use "telnet smtp.xxx.com 25" to connect smtp server, so what is  next step?
Thanks!

---

### Post by nanotube on 2006-05-25
next step is to start using smtp commnads. here is the complete RFC for smtp: [http://www.ietf.org/rfc/rfc0821.txt](http://www.ietf.org/rfc/rfc0821.txt). (starting with page 19, smtp commands, is a good idea).
so once you get a telnet connection, start with "helo yourservername", and go on.
this is another (probably easier to understand) link and examples: [http://cr.yp.to/smtp.html](http://cr.yp.to/smtp.html)

have fun. :)

---

### Post by mellibra on 2006-05-25
Thanks! :)

---

### Post by nanotube on 2006-05-25
you're welcome. ;) i remember back in the day i used to send email and browse the web through telnet... ah, those were the days. ..

---

### Post by nanotube on 2006-05-25
oh and by the way, your subject line also asks about receiving email through pop. to do that, you telnet to port 110, and then use the pop protocol (which is different from the smtp protocol). iirc, first you specify user with command USER username
then password with
PASS password
then to list messages i think it's 
LIST

but anyway, you can get the full specification for pop protocol if you search google. there is also of course command HELP which lists available commands - so it's something to rely on when you are not sure what's next. and works in both pop and smtp, btw.

---

