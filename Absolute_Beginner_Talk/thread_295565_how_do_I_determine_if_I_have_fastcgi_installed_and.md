---
title: "how do I determine if I have fastcgi installed and its being used by apache2?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by don7777 on 2006-11-08
Hi all,

I'm running ubuntu 6.06 with apache2.

How can I determine if I have fastcgi installed? And, how can I determine if apache2 is using it?

When I run "dpkg --get-selections | grep cgi" I see libfcgi-perl installed. Is this the same thing as fastcgi? If not, what else do I need? If so, How can I determine if apache2 is using it?

Thanks for any help,
Don

---

### Post by bsussman on 2006-11-08
> **don7777 said:**
> Hi all,

I'm running ubuntu 6.06 with apache2.

How can I determine if I have fastcgi installed? 

the output of phpinfo() lists all the modules currently in use.

---

