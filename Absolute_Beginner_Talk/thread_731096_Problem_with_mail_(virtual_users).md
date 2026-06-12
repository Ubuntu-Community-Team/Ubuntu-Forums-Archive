---
title: "Problem with mail (virtual users)"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by napi on 2008-03-21
Hi all,

Am trying to get emailing going on my server. I have 2 domains, 1stdomain.com and 2nddomain.com.

Have read a lot of stuff about postfix, and then decided to try the setup used in 

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

as it seems most closely linked to what I want. (Some users will have linux accounts, some won't etc)

All goes fine until testing it. I send an email to one of the accounts I've setup in the vmaps, but then when I go to the vmail directory, there's nothing there. It says that it should create the directory structure when an email is sent to that account but am getting nothing.

But, when I send an email to my account name, it appears in my own Maildir folder (/home/napi/Maildir/new).

Any thoughts? When I send the email as shown in that HowTo, I don't get any error or anything.

Any help is greatly appreciated :)

---

### Post by napi on 2008-03-22
Update on this;

Still not making any progress. The emails are being left in the postfix queue but not going anywhere even with attempted forced delivery. Not getting any errors in any of the log files for it.

---

