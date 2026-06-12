---
title: "Taking Ubuntu to another Level"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by markbusu on 2008-03-03
Hi,

So i managed to get Ubuntu up and running and believed have covered most of the basics...

Now the next step is trying to run Mailbox Server / MTA / DNS Server on my Ubuntu Machine.

What MTA / MailServer do you recommened to run on Ubuntu... and also what DNS Server?

Thanks!

---

### Post by ruy_lopez on 2008-03-03
MTA-->Postfix

DNS-->BIND

pop/imap-->dovecot

Depending on your requirements BIND might be overkill. /etc/hosts works fine for me, or dnsmasq.

---

### Post by Oldsoldier2003 on 2008-03-03
> **markbusu said:**
> Hi,

So i managed to get Ubuntu up and running and believed have covered most of the basics...

Now the next step is trying to run Mailbox Server / MTA / DNS Server on my Ubuntu Machine.

What MTA / MailServer do you recommened to run on Ubuntu... and also what DNS Server?

Thanks!well I'd run them on a server instead of the desktop, but i would use Bind for the DNS and probably one of the standard sendmail variants for mail since the support is there if you have questions on configuration... Postfix maybe?

---

### Post by markbusu on 2008-03-03
Indeed, I have more then one Machine running Ubuntu... however this is just a test Home Environment just to get hand on on the feel for Linux on Enterprise...

Anyway... thanks for feedback... will get right on it!

---

