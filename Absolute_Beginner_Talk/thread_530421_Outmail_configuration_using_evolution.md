---
title: "Outmail configuration using evolution"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-20
While sending outmails (using evolution)i am getting the following error message

Host lookup failed: gmail: Name or service not known


Any help

pkj

---

### Post by schorsch on 2007-08-20
You should enter the following address as SMTP server

```
smtp.gmail.com
```

Take a look at [this page]("http://http://mail.google.com/support/bin/topic.py?topic=1555"); choose one email-client and change the options in evolution accordingly.

---

### Post by Elf on horseback on 2007-08-20
Did you go in to your gmail settings and turn on POP3 mail?

---

### Post by pkj on 2007-08-20
I have entered smtp.gmail.com and have also enabled POP3 in Gmail settings...

I have no problem in retrieving my mails from Gmail...Only problem is that i am unable to send mails via Evolution

pkj

---

### Post by wgandhi on 2007-12-16
Hi,

I had the same problem as pkj. It turns out that u have to be really careful how you type in the server name in evolution. I had a space after the name. That prevented me from sending any email!
After making sure my hostname (smtp.gmail.com) was typed in without any space and the security type was TLS, everything worked as expected..
Hope this helps.

-Wish

---

### Post by S0VERE1GN on 2008-05-09
ok, so i changed my server to smtp.gmail.com, but a warning still comes up that says that my host is incorrect. what do i do?!?!?!?

---

