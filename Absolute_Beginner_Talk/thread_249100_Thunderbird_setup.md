---
title: "Thunderbird setup"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-02
I am trying to set up 2 email accounts in Thunderbird. My first one is from adelphia.net I have a problem when I get to  select the inoming mail server I pick the POP options and then the name of server which I got from adelphia's website mail.adelphia.net When I enter that it tells me please add a valid hostname:(  I also tried this with gmail. What am I doing wrong?

---

### Post by _simon_ on 2006-09-02
They usually start with pop.

e.g. 

Gmail Server name is pop.gmail.com
Username is your full email address.

---

### Post by Maddoguk2 on 2006-09-02
Try change from POP to IMAP. I had the same problem with my E-mail until I started using the IMAP and it worked.

---

### Post by HdK on 2006-09-02
still saying not a valid hostname:(

---

### Post by james99 on 2006-09-02
Im having the same issues, re pop mail. I suspect it may be a ISP issue.

---

### Post by Maddoguk2 on 2006-09-02
Did you put POP in front? If so then take it off because the mail. part of it depends on the server. Most server do use the POP prefix but some don't.

---

### Post by HdK on 2006-09-02
what do you mean mail.gmail.com bc that does not work I already tried,im getting very frustrated

---

### Post by kaamos on 2006-09-02
The email provider almost always has instructions for pop/imap access. Like [http://mail.google.com/support/bin/answer.py?answer=38343&topic=1555](http://mail.google.com/support/bin/answer.py?answer=38343&topic=1555)

---

### Post by _simon_ on 2006-09-02
For gmail you need the following (I know because this works for me)

POP (Incomming)

Server name: pop.gmail.com
Username: full email address e.g. [email]joe.bloggs@gmail.com[/email]
Port: 995
Security: SSL

SMTP (Outgoing)

Server name: smtp.gmail.com
Port 25
Username: full email address e.g. [email]joe.bloggs@gmail.com[/email]
Security: TLS

---

### Post by HdK on 2006-09-02
thank you simon

---

