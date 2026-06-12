---
title: "EMail on Linux"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by LAF4U on 2007-04-13
Hi,

This is probably to advanced for this forum, but I'll ask anyway.

I want to configure Ubuntu Email software to allow it to retrieve my Emails from the Microsoft Exchange Server that we have here at work. Is this possible to do? If so, where and what do I start with?

Thanks,

LAF4U

---

### Post by dbott67 on 2007-04-13
EDIT:  Just found this document:
[http://ubuntu-tutorials.com/2006/10/24/use-evolution-with-microsoft-exchange-ubuntu-606-610/](http://ubuntu-tutorials.com/2006/10/24/use-evolution-with-microsoft-exchange-ubuntu-606-610/)

###############################################################

I'm not an Exchange user myself, so there may be some proprietary MS stuff going on in the background for Calendaring, Scheduling and Offline caching, etc. but for simple e-mail, you should be able to get connected.

You need to ask your sys admins for the IP or FQDN name of the mail server (typically mail.yourdomain.com or pop3.yourdomain.com or smtp.yourdomain.com, etc.) and plug those into Evolution, Thunderbird or any other mail client under "Account Settings".

You also need to ask them if you should use POP3 or IMAP protocol (POP3 downloads the mail to your computer, while IMAP keeps everything on the server... very useful if you have some sort of webmail access or use multiple computers).

Hope this helps.

-Dave

---

### Post by LAF4U on 2007-04-13
Thanks Dave,

I will try to ask the sysadmin those questions. I don't know if they will collaborate though. After all the point here is to get away from WINDOWS and use Ubuntu LIVE CD to boot.

They won't like that :-)

---

### Post by compmodder26 on 2007-04-13
There is an exchange connector for evolution in the repositories.  If you have a web interface to get into your exchange e-mail, the connector should work.  It works on my machine.  It's a bit slow when you first start evolution, but it gets the job done.

---

